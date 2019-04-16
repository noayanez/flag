<template>
  <div
    class="uk-width-1-1 uk-height-1-1"
    style="padding-top: 70px;">
    <div
      class="uk-width-1-1 uk-flex uk-flex-middle uk-flex-center uk-padding-large@s uk-pading-remove-right uk-pading-remove-left uk-pading-remove-bottom"
      style="height:100%;">
      <div class="uk-width-1-3@m uk-width-1-1 uk-height-1-1 uk-flex uk-flex-middle">
        <div class="uk-width-1-1 uk-height-1-1 uk-flex uk-flex-column uk-flex-center uk-flex-middle container2 uk-visible@s">
          <div class="uk-height-1-1 uk-flex uk-flex-column uk-flex-center uk-flex-middle">
            <div class="uk-width-1-1">
              <a
                class=""
                style="padding-bottom: 20px;"
                @click="remove">
                <img
                  src="boton-flecha.png"
                  alt="...">
              </a>
            </div>
            <div
              class=""
              style="padding: 20px 0 10px 0">
              <div class="">
                <h3
                  style="color:white; font-weight: bold;"
                  class="title-font title-into-service uk-text-uppercase">{{ service.singleServiceName }}</h3>
              </div>
              <div>
                <ul
                  v-for="(el,key) in service.singleServiceItems"
                  :key="key"
                  class="uk-margin-remove">
                  <li
                    class="color"
                    style="">
                    <span class="subtitle-font">{{ el.singleServiceItem }}</span>
                  </li>
                </ul>
              </div>
            </div>
            <div
              class=""
              style="">
              <a
                style="text-decoration: none; color:#303e48"
                @click="goTo(`${service.singleServiceRedirect}`, `${service.singleServiceButton }`)">
                <div class="uk-width-auto@s uk-width-1-1 uk-flex uk-flex-center uk-flex-middle">
                  <div
                    class="uk-text-center uk-flex uk-flex-center uk-flex-middle"
                    style="font-family: futura; font-weight: 800; color: #000000cc; font-size: 1rem; background-image: url('/boton-1.png'); background-repeat: no-repeat; background-size: cover; height: 81px; width: 180px; cursor: pointer;">
                    {{ service.singleServiceButton }}
                  </div>
                </div>
              </a>
            </div>
          </div>
        </div>
        <div class="uk-hidden@s uk-height-1-1 uk-flex uk-flex-column uk-flex-right uk-flex-middle">
          <h2
            class="uk-width-1-1 uk-text-center"
            style="color:white; font-weight: bold; margin-bottom: 10px;">{{ service.singleServiceName }}</h2>
          <div
            class="uk-width-1-1"
            style="padding-bottom: 30px;">
            <div
              :style="`background-image: url(${service.serviceIntoImage};`"
              class="uk-width-1-1"
              style="background-position: 50% 50%;background-size: cover; padding: 15px 0px; margin-bottom: 10px;position:relative">
              <div
                class="gradient"
                style="height:100%;width:100%; position:absolute;top:0;"/>
              <div style="padding-left: 15px; z-index:100; position: relative;">
                <ul
                  v-for="(el,key) in service.singleServiceItems"
                  :key="key"
                  style="margin: 10px;">
                  <li class="color">
                    <div
                      style="color: white; font-weight: 800 !important; font-size: 18px;">{{ el.singleServiceItem }}</div>
                  </li>
                </ul>
              </div>
            </div>
            <div class="uk-width-1-1 uk-flex uk-flex-center uk-flex-middle">
              <a
                style="text-decoration: none;color:#303e48"
                @click="goTo(`${service.singleServiceRedirect}`, `${service.singleServiceButton }`)">
                <div
                  class="button-services uk-flex uk-flex-center uk-flex-middle"
                  style="width: 200px; height: 90px;">
                  {{ service.singleServiceButton }}
                </div>
              </a>
            </div>
          </div>

        </div>
      </div>
      <div
        :style="`background-image: url(${service.serviceIntoImage};`"
        class="uk-width-2-3@m uk-width-1-1 uk-height-1-1 uk-align-center containerImageInto uk-visible@s"/>
    </div>
  </div>
</template>

<script>
import { mapGetters} from 'vuex'

var UIkit

if (process.browser) {
  UIkit = require('uikit')
}

export default {
  data(){
      return{
          service:{}
      }
  },
    computed: {
  ...mapGetters({
      content: 'getIntoService'
  })},
  async mounted() {
  // HERE IS WHERE THE FETCHED INFORMATION IS DISTRIBUTED
    // await wait(1000)
    //console.log(this.content)
    this.service = this.content
  },
  methods:{
    remove(){
      this.$router.app.$store.commit('SET_DATA_SERVICES','')
      console.log("clicked");
      this.$emit('clicked')
      // console.log(this.content)
    },
    goTo (section, label) {
      UIkit.offcanvas('#offcanvas-nav-primary').hide().then(() => {
        //Validate screeen size
        UIkit.scroll({offset: 0}).scrollTo(section)
      })
    }
  }
}
function wait(n) {
   return new Promise(function(resolve, reject) {
    setTimeout(() => {
      resolve()
    }, n)
  })
}
</script>

<style scope>
.title-font {
  font-size: 1.5rem;
  margin: 0 !important;
}
.gradient {
  /* Permalink - use to edit and share this gradient: http://colorzilla.com/gradient-editor/#000000+0,000000+100&0.65+0,0.71+100;Neutral+Density */
  background: -moz-linear-gradient(top, rgba(0,0,0,0.65) 0%, rgba(0,0,0,0.71) 100%); /* FF3.6-15 */
  background: -webkit-linear-gradient(top, rgba(0,0,0,0.65) 0%,rgba(0,0,0,0.71) 100%); /* Chrome10-25,Safari5.1-6 */
  background: linear-gradient(to bottom, rgba(0,0,0,0.65) 0%,rgba(0,0,0,0.71) 100%); /* W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+ */
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#a6000000', endColorstr='#b5000000',GradientType=0 ); /* IE6-9 */
}
.containerImageInto {
  min-width: 400px;
  background-size:cover;
  background-position:50% 50%;
  height:80%;
  border-radius: 30px 0px 0px 30px;
}
.title-into-service {
  width: 40%;
}
.color {
  color: #faeb05;
  font-size: 1.2rem;
  font-weight: bold;
  padding: 10px 0 10px 0;
}
@media (max-height: 600px) {
  .color {
    color: #faeb05;
    font-size:16px;
    font-weight: bold;
    padding: 5px 0;
  }
}
@media (max-width: 600px) {
  .color {
    color: #faeb05;
    font-size: 20px;
    font-weight: bold;
    padding: 0 !important;
  }
}
.color > span{
  color: white;
}
.button-service2{
  background: url(/boton-1.png) no-repeat;
  background-size: 100%;
  padding: 35px 122px 37px 30px;
  text-decoration: none;
  color: #303e48;
  font-weight: bold;
  width: 13%;
  font-size: 18px;
}
.container2{
  width: 40vw;
}
@media(max-width: 769px){
  .button-service2{
    padding: 33px 130px 37px 27px;
  }
}
@media (max-width: 420px){
  .container2{
    width: 100%;
    padding: 0;
  }
  .button-service{
    padding: 35px 103px 38px 54px;
    margin: auto;
  }
  .button-service2{
    padding: 35px 135px 32px 30px;
    margin: auto;
  }
}
</style>
