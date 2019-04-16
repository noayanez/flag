<template>
  <div
    id="Services"

    class="uk-position-relative services-responsive">
    <div
      class="uk-height-1-1 bkg-animate"
      style="background-image: url('/trama.png');background-size:cover;background-position:50% 50%; width: 100%; position: absolute; background-color:#303e47;background-blend-mode: overlay;"/>
    <div
      class="uk-flex uk-flex-center uk-width-1-1 uk-position-absolute flexeador gradient-services uk-height-1-1">
      <transition
        name="slide-fade">
        <div
          v-if="content=='' && flag"
          class="services-width services-height uk-flex uk-flex-column uk-flex-center@m uk-flex-right uk-flex-middle"
          style="">
          <div
            class="titleServices uk-flex uk-flex-center uk-flex-middle"
            style="">
            <h2 class="title-services uk-margin-remove">{{ services.serviceSectionTitle }}</h2>
          </div>
          <div class="delimiter container-heighter">
            <div
              v-if="services.service"
              class="uk-visible@s uk-flex uk-flex-center uk-flex-middle uk-height-1-1">
              <div
                v-for="(ele, key) in services.service"
                :key="key"
                class="uk-width-1-2 uk-padding-small uk-height-1-1 uk-padding-remove-bottom"
                style="text-align:center;">
                <div
                  :style="`background-image: url(${ele.singleService.singleServiceImage};`"
                  class="uk-height-1-1 uk-align-center containerImage"
                  style="cursor:pointer;"
                  @click="getContent(ele.singleService.singleServiceName)"/>
                <div class="uk-width-1-1 uk-flex uk-flex-center uk-flex-middle">
                  <a
                    style="text-decoration: none;color:#303e48"
                    @click="getContent(ele.singleService.singleServiceName)">
                    <div
                      class="button-services uk-flex uk-flex-center uk-flex-middle"
                      style="width: 200px; height: 90px;">
                      {{ ele.singleService.singleServiceName }} </div></a>
                </div>
              </div>
            </div>
            <div class="uk-hidden@s uk-flex uk-flex-center uk-flex-middle uk-width-1-1">
              <div
                uk-slideshow="animation: slide; autoplay: true; autoplay-interval: 4000;"
                class="uk-width-1-1">
                <div
                  class="uk-position-relative uk-visible-toggle">
                  <ul
                    class="uk-slideshow-items imager"
                    style="">
                    <li
                      v-for="(ele, key) in services.service"
                      :key="key"
                      class="imager">
                      <div
                        :style="`background-image: url(${ele.singleService.singleServiceImage});`"
                        style="margin-bottom: 10px !important"
                        class="imager2 uk-align-center container-slider"/>
                      <div class="uk-width-1-1 uk-flex uk-flex-center uk-flex-middle">
                        <a
                          style="text-decoration: none;color:#303e48"
                          @click="getContent(ele.singleService.singleServiceName)">
                          <div
                            class="button-services uk-flex uk-flex-center uk-flex-middle"
                            style="width: 200px; height: 90px;">
                            {{ ele.singleService.singleServiceName }} </div></a>
                      </div>
                      <!-- <a
                        style="text-decoration: none;color:#303e48"
                        @click="getContent(ele.singleService.singleServiceName)">
                        <div
                          class="button-slider"
                          style="">
                          {{ ele.singleService.singleServiceName }} </div></a> -->
                    </li>
                  </ul>
                  <ul
                    class="uk-slideshow-nav uk-dotnav uk-flex-center"
                    style="padding: 0px !important; margin-bottom: 20px;"/>
                </div>
              </div>
            </div>
          </div>
        </div>
      </transition>
      <transition name="slide-fade">
        <IntoService
          v-if="content!=='' && flag2"
          :service="intoService"
          @clicked="hidde"/>
      </transition>
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
        device:'',
        flag:true,
        flag2:false
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
        this.show()
       //  console.log(this.$store.state.dataService)
      },
      async show(){
        console.log('################');
        console.log(this.flag +" "+ this.flag2);
        this.flag = !this.flag
        await wait(500)
        this.flag2 = !this.flag2
        console.log("funcion show");
        console.log(this.flag +" "+ this.flag2);
      },
      async hidde(){
        console.log('################');
        console.log(this.flag +" "+ this.flag2);
        this.flag2 = !this.flag2
        await wait(500)
        this.flag = !this.flag
        console.log("funcion show");
        console.log(this.flag +" "+ this.flag2);
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
@import url(https://cdn.jsdelivr.net/npm/animate.css@3.5.2/animate.min.css);
.imager {
  height: calc(50vh + 130px);
}
imager2 {
  height: 50vh;
}
@media (max-width: 400px) {
  .imager {
    height: calc(45vh + 130px);
  }
  imager2 {
    height: 40vh;
  }
}
@media (max-width: 359px) {
  .imager {
    height: calc(40vh + 130px);
  }
  imager2 {
    height: 40vh;
  }
}
.container-heighter {
  width: 100%;
}
@media (max-height: 600px) and (min-width: 1300px) {
  .container-heighter {
    width: 60%;
  }
}
.flexeador {
  align-items: center;
}
@media (max-height: 800px) and (max-width: 500px) {
  .flexeador {
    align-items: flex-end;
  }
}
@media (max-height: 800px) {
  .flexeador {
    align-items: flex-end;
  }
}
.gradient-services {
  /* Permalink - use to edit and share this gradient: http://colorzilla.com/gradient-editor/#3b4750+1,000000+100&0.65+0,0+100 */
  background: -moz-linear-gradient(top, rgba(59,71,80,0.65) 0%, rgba(59,71,80,0.64) 1%, rgba(0,0,0,0) 100%); /* FF3.6-15 */
  background: -webkit-linear-gradient(top, rgba(59,71,80,0.65) 0%,rgba(59,71,80,0.64) 1%,rgba(0,0,0,0) 100%); /* Chrome10-25,Safari5.1-6 */
  background: linear-gradient(to bottom, rgba(59,71,80,0.65) 0%,rgba(59,71,80,0.64) 1%,rgba(0,0,0,0) 100%); /* W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+ */
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#a63b4750', endColorstr='#00000000',GradientType=0 ); /* IE6-9 */
}
.flex-bottom{
  align-items: center;
}

.slide-fade-enter-active {
  transition: all 0.5s ease;
}
.slide-fade-leave-active {
  transition: all 0.5s ease;
}
.slide-fade-leave, .slide-fade-leave-active {
  opacity: 1;
}
.slide-fade-enter, .slide-fade-leave-active {
  opacity: 0;
}
.services-responsive{
  min-height:100vh;
}
@media(min-height: 1000px){
  .services-responsive{
    min-height: 0px;
    height:800px;
  }
}
.container-devices {
  height: 737px;
}
.services-width{
  width: 65%;
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
  background-size: 100%;
  text-decoration: none;
  color: #303e48;
  text-align: center;
  font-weight: bold;
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
  width: 100%;
  background-size:cover;
  background-position:50% 50%;
  height:50vh;
  border-radius: 30px;
  margin-bottom:10px;
}
@media (max-width: 600px) {
  .containerImage {
    margin: 0 !important
  }
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

@media(max-width: 1369px){
  .containerImage{
    height: 50vh;
  }
  .button-services{
  }
  .services-width{
    width: 75%;
  }
  .flex-bottom{
    align-items: flex-end;
  }
}
@media(max-height: 700px){
  .flex-bottom{
    align-items: flex-end;
  }
}
@media (max-width: 1024px){
  .containerImage{
    height:35vh;
}
.container-height{
   height:80vh;
}
.services-width{
  width: 85%;
}
.flex-bottom{
    align-items: flex-end;
  }
}
.services-height {
  height: 80%;
  padding-top: 40px;
}
@media (max-height: 700px){
  .services-height {
    height: 80%;
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
    height: 41vh;
  }
}
@media (max-width: 420px){
  .titleServices{
    height:20%;
    text-align: center;
    padding-top: 17px;
    padding-bottom: 12px;
    align-items: flex-end;
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
  .services-width{
    width: 100%;
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
