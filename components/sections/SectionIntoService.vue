<template>
  <div>
    <img 
      src="boton-flecha.png" 
      alt="..."
      class="uk-hidden@s"
      style="position: relative;top: 0px;">
    <div 
      class="uk-flex uk-flex-wrap"
      style="padding-top: 30px;">
      <h2 
        class="uk-hidden@s uk-padding-small"
        style="color:white;width: 50%;margin: auto;font-weight: bold;">{{ service.singleServiceName }}</h2>
      <div class="uk-width-1-2@m uk-width-1-1 uk-padding-large container2">
        <a 
          class="uk-visible@s"
          style="padding-bottom: 20px;"
          @click="remove">
          <img 
            src="boton-flecha.png" 
            alt="...">
        </a>
        <!-- view web -->
        <div 
          class="uk-flex uk-flex-column uk-visible@s"
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
          <div
            style="padding-top: 30px;">
            <a
              class="button-service uk-text-uppercase" 
              style="text-decoration: none;color:#303e48"
            >{{ service.singleServiceButton }}</a>
          </div>
        </div>
        <!-- responsive view   -->
        <div
          class="uk-hidden@s" 
          style="padding-bottom: 30px;">
          <div
            :style="`background-image: url(${service.serviceIntoImage};`"
            style="background-position: 50% 50%;background-size: cover; padding: 15px 0px"> 
            <div style="padding-left: 15px">
              <ul 
                v-for="(el,key) in service.singleServiceItems"
                :key="key"> 
                <li class="color"><span>{{ el.singleServiceItem }}</span></li>
              </ul>
            </div>
          </div>
          <a style="text-decoration:none; color:#314049;">
            <div class="button-service">
              {{ service.singleServiceButton }}
            </div>
          </a>
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
  padding: 35px 48px 44px 60px;
  text-decoration: none;
  color: #303e48;
  font-weight: bold;
  width:20%; 
  margin:auto
}
.container2{
  width: 40%;
}
@media (max-width: 420px){
  .container2{
    width: 100%;
    padding: 0;
  }
  .button-service{
      padding: 35px 103px 38px 54px;
}
}
</style>
