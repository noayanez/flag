<template>
  <div 
    id="Events"
    style="background-image: url(/tramas.png);background-size:cover;background-position:50% 50%; width:100%; heigth:100%; background-color:#303e48;"
    class=" uk-height-1-1">
    <div v-if="content == ''">
      <div
        class="uk-padding titleServices" 
        style="text-align:center;">
        <h2 class="title-services"> {{ services.serviceSectionTitle }} </h2>
      </div>
      <div 
        v-if="services.service"
        class="uk-flex uk-flex-wrap uk-flex-center uk-height-1-1 container-services">
        <div
          v-for="(ele, key) in services.service"
          :key="key"
          class="uk-width-1-2@m uk-width-1-1 uk-padding-small uk-height-1-1 uk-visible@s"
          style="text-align:center; padding-bottom: 40px;">
          <div
            :style="`background-image: url(${ele.singleService.singleServiceImage};`"
            class="uk-height-1-1 uk-padding uk-align-center containerImage"/>
          <a
            style="text-decoration: none;color:#303e48"
            @click="getContent(ele.singleService.singleServiceName)">
            <div 
              class="button-portrait"
              style="">
              {{ ele.singleService.singleServiceName }} </div></a>
        </div>
      </div>
      <div class="uk-hidden@s">
        <div uk-slideshow="animation: slide; autoplay: true; autoplay-interval: 4000; min-height: 490; max-height: 600">
          <div 
            class="uk-position-relative uk-visible-toggle">
            <ul class="uk-slideshow-items">
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
        intoService:''
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
                  singleServiceButton: el.singleService.singleServiceButton
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

<style scope>
.img-services{
    border-radius: 20px;
}
.title-services{
    font-weight: bold;
    color: white;
}
.button-portrait{
  background: url('/boton-1.png') no-repeat;
  background-size: cover;
  padding: 25px 33px 10px 33px;
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
.container-services{
    width: 60%; 
    margin:auto;
}
@media (max-width: 1024px){
  .containerImage{
    min-width: 350px;
    height:35vh;
}
.container-services{
    width: 90%; 
    margin:auto;
}
.button-portrait{
  padding: 25px 45px 18px 45px;
}
}
@media (max-width: 420px){
  .button-portrait{
    background: url('/boton-1.png') no-repeat;
    background-size: cover;
    padding: 25px 30px;
    text-decoration: none;
    color: #303e48;
    font-weight: bold;
    width:50%;
    margin:auto
}
  .containerImage{
    min-width: 250px;
 }
  .container-services{
    width: 100%;
 }
 .titleServices{
     padding-bottom: 10px !important;
 }
 .uk-dotnav > * > * {
    width: 15px;
    height: 15px;
}
.uk-dotnav > .uk-active > * {
  background-color: #faeb00;
  }
}
</style>
