<template>
  <div class="uk-flex uk-flex-wrap">
    <div class="uk-width-1-2@m uk-width-1-1 uk-padding container2">
      <a 
        style="padding-left: 60px"
        @click="remove">
        <img 
          src="boton-flecha.png" 
          alt="...">
      </a>
      <div class="uk-flex uk-flex-column uk-padding-large">
        <div>
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
        <div
          style="padding-top: 30px;">
          <a
            class="button-service uk-text-uppercase" 
            style="text-decoration: none;color:#303e48"
          >{{ service.singleServiceButton }}</a>
        </div>
      </div>
    </div>
    <div
      :style="`background-image: url(${service.serviceIntoImage};`"
      class="uk-width-1-2@m uk-height-1-1 uk-padding uk-align-center containerImageInto"/>
  </div>
</template>

<script>
import { mapGetters} from 'vuex'


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
    height:65vh;
    width: 60%;
    border-radius: 30px;
}
.title-into-service{
    width: 40%;
}
.color{
    color: #faeb05;
    font-size: 18px;
    font-weight: bold;
}
.color > span{
    color: white;
}
.button-service{
  background: url('/boton-1.png') no-repeat;
  background-size: cover;
  padding: 30px 50px 20px 50px;
  text-decoration: none;
  color: #303e48;
  font-weight: bold;
}
.container2{
  width: 40%;
}
</style>
