<template>
  <div class="uk-height-1-1">
    <div 
      class="uk-flex uk-flex-middle uk-flex-center uk-padding-large@s uk-pading-remove-right uk-pading-remove-left uk-pading-remove-bottom"
      style="height:100%">
      <div class="uk-height-1-1 uk-flex uk-flex-center uk-flex-middle">
        <div class="uk-flex uk-flex-column uk-flex-middle uk-padding-large container2 uk-visible@s">
          <div>
            <a 
              class=""
              style="padding-bottom: 20px;"
              @click="remove">
              <img 
                src="boton-flecha.png" 
                alt="...">
            </a>
            <div 
              class=""
              style="padding: 20px 0px;">
              <div class="">
                <h3 
                  style="color:white;font-weight: bold;"
                  class="title-into-service uk-text-uppercase">{{ service.singleServiceName }}</h3>
              </div>
              <div>
                <ul 
                  v-for="(el,key) in service.singleServiceItems"
                  :key="key"
                  class="uk-margin-remove"> 
                  <li 
                    class="color"
                    style="padding: 8px 0px;"><span>{{ el.singleServiceItem }}</span></li>
                </ul>
              </div>
            </div>
            <div
              class=""
              style="">
              <a
                style="text-decoration: none;color:#303e48"
                @click="goTo(`${service.singleServiceRedirect}`, `${service.singleServiceButton }`)">
                <div 
                  class="button-service2"
                  style="">
                  {{ service.singleServiceButton }} </div></a>
            </div>
          </div>
        </div>
        <div class="uk-hidden@s uk-height-1-1">
          <h2 
            class="uk-padding-small uk-width-1-2"
            style="color:white;width: 50%;margin: auto;font-weight: bold;padding-top:20px;">{{ service.singleServiceName }}</h2>
          <div
            class="uk-width-1-1" 
            style="padding-bottom: 30px;">
            <div
              :style="`background-image: url(${service.serviceIntoImage};`"
              class="uk-width-1-1"
              style="background-position: 50% 50%;background-size: cover; padding: 15px 0px; margin-bottom: 10px;position:relative"> 
              <div 
                class="gradient"
                style="height:100%;width:100%; position:absolute;top:0;z-index:-1"/>
              <div style="padding-left: 15px; z-index:100;">
                <ul 
                  v-for="(el,key) in service.singleServiceItems"
                  :key="key"> 
                  <li 
                    class="color"><span>{{ el.singleServiceItem }}</span></li>
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
                  {{ service.singleServiceButton }}</div></a>
            </div>
          </div>

        </div>
      </div>
      <div
        :style="`background-image: url(${service.serviceIntoImage};`"
        class="uk-width-1-2@m uk-height-1-1 uk-align-center containerImageInto uk-visible@s"/>
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
        UIkit.scroll({offset: 80}).scrollTo(section)
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
.gradient {
    /* Permalink - use to edit and share this gradient: http://colorzilla.com/gradient-editor/#000000+0,000000+100&0.65+0,0.71+100;Neutral+Density */
background: -moz-linear-gradient(top, rgba(0,0,0,0.65) 0%, rgba(0,0,0,0.71) 100%); /* FF3.6-15 */
background: -webkit-linear-gradient(top, rgba(0,0,0,0.65) 0%,rgba(0,0,0,0.71) 100%); /* Chrome10-25,Safari5.1-6 */
background: linear-gradient(to bottom, rgba(0,0,0,0.65) 0%,rgba(0,0,0,0.71) 100%); /* W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+ */
filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#a6000000', endColorstr='#b5000000',GradientType=0 ); /* IE6-9 */
  }
.containerImageInto{
    min-width: 400px;
    background-size:cover; 
    background-position:50% 50%; 
    height:80%;
    width: 60vw;
    border-radius: 30px 0px 0px 30px;
}
.title-into-service{
    width: 40%;
}
.color{
    color: #faeb05;
    font-size: 24px;
    font-weight: bold;
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
