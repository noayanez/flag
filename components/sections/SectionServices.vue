<template>
  <div 
    id="Services"
    :class="device ? 'container-devices' : 'uk-height-viewport'"
    class="uk-height-1-1 bkg-animate uk-position-relative uk-flex uk-flex-center uk-flex-middle"
    style="background-image: url(/trama.png);background-size:cover;background-position:50% 50%; width:100%; background-color:#303e47;background-blend-mode: overlay;">
    <div 
      v-if="content == ''"
      class="">
      <div
        class="uk-padding@s titleServices uk-height-1-1" 
        style="text-align:center;">
        <h2 class="title-services"> {{ services.serviceSectionTitle }} </h2>
      </div>
      <div class="">
        <div 
          v-if="services.service"
          class="uk-flex uk-flex-wrap uk-flex-center uk-height-1-1">
          <div
            v-for="(ele, key) in services.service"
            :key="key"
            class="uk-width-1-2 uk-padding-small uk-height-1-1 uk-visible@s"
            style="text-align:center; padding-bottom: 40px;">
            <div
              :style="`background-image: url(${ele.singleService.singleServiceImage};`"
              class="uk-height-1-1 uk-padding uk-align-center containerImage"/>
            <a
              style="text-decoration: none;color:#303e48"
              @click="getContent(ele.singleService.singleServiceName)">
              <div 
                class="button-services"
                style="">
                {{ ele.singleService.singleServiceName }} </div></a>
          </div>
        </div>
        <div class="uk-hidden@s uk-height-viewport">
          <div 
            uk-slideshow="animation: slide; autoplay: true; autoplay-interval: 4000;"
            class="height">
            <div 
              class="uk-position-relative uk-visible-toggle">
              <ul 
                class="uk-slideshow-items slideshow-height">
                <li 
                  v-for="(ele, key) in services.service"
                  :key="key">
                  <div 
                    :style="`background-image: url(${ele.singleService.singleServiceImage});`"
                    style=""
                    class="uk-height-1-1 uk-padding uk-align-center container-slider"/>
                  <a
                    style="text-decoration: none;color:#303e48"
                    @click="getContent(ele.singleService.singleServiceName)">
                    <div 
                      class="button-slider"
                      style="">
                      {{ ele.singleService.singleServiceName }} </div></a>
                </li>
              </ul>
              <ul 
                class="uk-slideshow-nav uk-dotnav uk-flex-center"
                style="padding-bottom: 40px;"/>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div v-else>
      <IntoService 
        :service="intoService"/>
    </div>
    

  </div>
</template>

<script>

import { mapGetters} from 'vuex'

import IntoService from '~/components/sections/SectionIntoService.vue'

export default {
    components:{
      IntoService
    },
    props:{
        services:{
            type: Object,
            default: function(){
                return {message:'events'}
            }
        }
    },
    data(){
      return{
        intoService:'',
        device:''
      }
    },
    computed: {
    ...mapGetters({
        content: 'getIntoService'
    })},
    mounted(){
     var userAgent = navigator.userAgent || navigator.vendor || window.opera
    if (/iPad|iPhone|iPod/.test(userAgent) && !window.MSStream) {
      this.device = true
    }
  },
    async mounted() {
    // HERE IS WHERE THE FETCHED INFORMATION IS DISTRIBUTED
      await wait(1000)
      //console.log(this.content)
      this.intoService = await this.content
    },
    methods:{
      getContent(e){
        this.services.service.forEach(el => {
            if (el.singleService.singleServiceName == e){
               this.$router.app.$store.commit(
                'SET_DATA_SERVICES',
                {
                  singleServiceName: el.singleService.singleServiceName,
                  serviceIntoImage: el.singleService.serviceIntoImage,
                  singleServiceItems: el.singleService.singleServiceItems,
                  singleServiceButton: el.singleService.singleServiceButton,
                  singleServiceRedirect: el.singleService.singleServiceRedirect
                }
              );


            }
        });
        this.intoService = this.content
       //  console.log(this.$store.state.dataService)
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

<style>
.container-devices {
  height: 737px;
}
.img-services{
    border-radius: 20px;
}
.title-services{
    font-weight: bold;
    color: white;
}
.padding-top{
  padding-top:170px;
}
.button-services{
  background: url('/boton-1.png') no-repeat;
  background-size: cover;
  padding: 30px 68px 20px 65px;
  text-decoration: none;
  color: #303e48;
  font-weight: bold;
  width:20%; 
  margin:auto
}
.button-slider{
  background: url('/boton-1.png') no-repeat;
  background-size: cover;
  padding: 28px 78px 28px 78px;
  text-decoration: none;
  color: #303e48;
  font-weight: bold;
  width:20%; 
  margin:auto
}
.containerImage{
    min-width: 400px;
    background-size:cover; 
    background-position:50% 50%; 
    height:48vh;
    width: 50%;
    border-radius: 30px;
}
.container-slider{
    background-size:cover; 
    background-position:50% 50%; 
    height: 45vh;
    width: 70%;
    border-radius: 30px;
}
.bkg-animate{
  -webkit-animation: slide 20s linear infinite;
  animation: slide 20s linear infinite;
}
@keyframes slide {
   from { background-position: 0 0; }
    to { background-position: -400px 0; }
}
 @-webkit-keyframes slide {
    from { background-position: 0 0; }
    to { background-position: -400px 0; }
  }
@media (max-width: 1024px){
  .containerImage{
    min-width: 350px;
    height:35vh;
}
.container-height{
   height:80vh;
}
}
@media (max-width: 769px){
   .container-height{
        height:100vh;
    }
    .padding-top{
        padding-top: 171px;
    }
    .containerImage {
      min-width: 327px;
      height: 41vh;
    }
    .button-services{
      padding: 25px 67px 16px 59px;
    }
}
@media (max-width: 420px){
  .containerImage{
    min-width: 250px;
 }
 .titleServices{
     padding-bottom: 10px !important;
 }
 .uk-dotnav > * > * {
    width: 15px;
    height: 15px;
 }
 .uk-dotnav{
   padding-top: 31px;
 }
 .slideshow-height{
    min-height: 450px !important;
}
.padding-top{
  padding-top:20px;
}

}
@media(min-width: 376px) and (max-width: 414px){
  .slideshow-height{
    min-height: 466px !important;
}
.titleServices{
     padding-bottom: 15px !important;
     padding-top: 20px !important;
     padding-left: 20px;
     padding-right: 20px;
 }
}

@media(min-width: 361px) and (max-width: 375px){
  .slideshow-height{
    min-height: 470px !important;
  }
  .container-slider{
    height: 50vh;
    width: 84%;
  }
  .titleServices{
     padding-bottom: 15px !important;
     padding-bottom: 20px !important;
      padding-left: 20px;
     padding-right: 20px;
 }
}
@media (max-width: 360px){
  .title-services{
    padding: 14px
  }
  .slideshow-height{
      min-height:417px !important;
}
}
@media (max-width:320px){
  .slideshow-height{
      min-height:380px !important;
}
.title-services{
    padding:0px !important;
  }
}

.uk-dotnav > .uk-active > * {
  background-color: #faeb00 !important;
  }
  .uk-dotnav > * > *{
    width: 15px;
    height: 15px;
    border: 1px solid #faeb00 ;
  }
</style>
