<template>
  <div>
    <a
      class="uk-hidden@s"
      style="position: relative;top: 0px;width:15%;"
      @click="remove">
      <img 
        src="boton-flecha.png" 
        alt="..."
        class="uk-hidden@s button-back">
    </a>
    <div 
      class="uk-flex uk-flex-wrap-stretch uk-flex-center uk-padding-large@s uk-pading-remove-right uk-pading-remove-left uk-pading-remove-bottom"
      style="">
      <div class="">
        <div class="uk-flex uk-flex-column uk-flex-middle uk-width-1-1 uk-padding-large container2">
          <div>
            <a 
              class="uk-visible@s"
              style="padding-bottom: 20px;"
              @click="remove">
              <img 
                src="boton-flecha.png" 
                alt="...">
            </a>
            <div 
              class="uk-visible@s"
              style="padding-top: 20px;">
              <div class="uk-visible@s">
                <h2 
                  style="color:white;font-weight: bold;"
                  class="title-into-service uk-text-uppercase">{{ service.singleServiceName }}</h2>
              </div>
              <div>
                <ul 
                  v-for="(el,key) in service.singleServiceItems"
                  :key="key"> 
                  <li class="color"><span>{{ el.singleServiceItem }}</span></li>
                </ul>
              </div>
            </div>
            <div
              class="uk-visible@s"
              style="padding-top: 30px;">
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
        <div>
          <h2 
            class="uk-hidden@s uk-padding-small uk-width-1-2"
            style="color:white;width: 50%;margin: auto;font-weight: bold;padding-top:20px;">{{ service.singleServiceName }}</h2>
          <div
            class="uk-hidden@s uk-width-1-1" 
            style="padding-bottom: 30px;">
            <div
              :style="`background-image: url(${service.serviceIntoImage};`"
              class="uk-width-1-1"
              style="background-position: 50% 50%;background-size: cover; padding: 15px 0px"> 
              <div style="padding-left: 15px">
                <ul 
                  v-for="(el,key) in service.singleServiceItems"
                  :key="key"> 
                  <li class="color"><span>{{ el.singleServiceItem }}</span></li>
                </ul>
              </div>
            </div>
            <a
              style="text-decoration:none; color:#314049;"
              @click="goTo(`${service.singleServiceRedirect}`, `${service.singleServiceButton }`)">
              <div class="button-service2">
                {{ service.singleServiceButton }}
              </div>
            </a>
          </div>

        </div>
      </div>
      <div
        :style="`background-image: url(${service.serviceIntoImage};`"
        class="uk-width-1-2@m uk-height-1-1 uk-padding uk-align-center containerImageInto uk-visible@s"/>
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
      await wait(1000)
      //console.log(this.content)
      this.service = this.content
    },
    methods:{
      remove(){
        this.$router.app.$store.commit('SET_DATA_SERVICES','')
        console.log(this.content)
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
.containerImageInto{
    padding-top: 60px;
    min-width: 400px;
    background-size:cover; 
    background-position:50% 50%; 
    height:auto;
    width: 60vw;
    border-radius: 30px;
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
   padding: 35px 122px 37px 40px;
    text-decoration: none;
    color: #303e48;
    font-weight: bold;
    width: 13%;
    font-size: 18px;
}
.container2{
  width: 40vw;
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
      padding: 36px 115px 37px 50px;
      margin: auto;
  }
}
</style>
