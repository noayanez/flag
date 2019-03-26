<template>
  <div 
    style="background-image: url(/tramas.png);background-size:cover;background-position:50% 50%; width:100%; heigth:100%; background-color:#303e48;"
    class="uk-height-viewport uk-height-1-1">
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
          class="uk-width-1-2@m uk-width-1-1 uk-padding-small uk-height-1-1"
          style="text-align:center; padding-bottom: 40px;">
          <div
            :style="`background-image: url(${ele.singleService.singleServiceImage};`"
            class="uk-height-1-1 uk-padding uk-align-center containerImage"/>
          <div 
            class="button-portrait"
            style="">
            <a
              style="text-decoration: none;color:#303e48"
              @click="getContent(ele.singleService.singleServiceName)">{{ ele.singleService.singleServiceName }}</a>
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
    color: black;
}
.button-portrait{
  background: url('/boton-1.png') no-repeat;
  background-size: cover;
  padding: 25px 30px 10px 30px;
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
.container-services{
    width: 60%; 
    margin:auto;
}
@media (max-width: 1024px){
  .containerImage{
    min-width: 320px;
    height:35vh;
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
}
</style>
