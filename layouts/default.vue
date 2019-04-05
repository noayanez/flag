<template>
  <div>
    <div v-if="content !== ''">
      <no-ssr>
        <Navbar/>
      </no-ssr>
      <nuxt />
      <no-ssr>
        <!-- <Footer /> -->
      </no-ssr>
    </div>
    <div
      v-else
      class="uk-flex uk-flex-column uk-flex-middle uk-flex-center uk-height-viewport"
      style="background-color:#303e47">
      <div class="pulse-btn">
        <img
          src="logo-principal.png"
          alt="Logo"> 
      </div>
      
    </div>
  </div>
</template>

<script>
import { mapState } from 'vuex'

import Navbar from '~/components/general/Navbar'
import Footer from '~/components/general/Footer'


export default {
  components : {
    Navbar,
    Footer
  },
  data(){
    return{
      content:''
    }
  },
    async mounted() {
    this.consumer()
  },
  methods:{
    async consumer(){
      try {
        this.content= await this.$axios.$get('/site/page')
        this.$router.app.$store.commit(
          'SET_DATA_VIEW',
          this.content
        )
        // console.log(this.$store.state.dataView)
      } catch (error) {
        console.log('error')
      }
    }
  }
}
</script>

<style>
h1,h2,h3,a,div{
  font-family: 'Futura';
  font-weight: 800 !important;
}
p,span,input,textarea{
  font-family: 'Futura';
  font-weight: 700 !important;
}
.pulse-btn {
    position: relative;
    margin:100px auto;
    width: 400px;
    height: auto;
    animation: pulse 2000ms infinite;
}
@keyframes pulse {
  0%, 100% {
     tranform: scale(1);
  }
  50% {
     transform: scale(1.2);
  }
}

</style>
