<template>
  <div>
    <div v-if="content != ''">
      <no-ssr>
        <Navbar/>
      </no-ssr>
      <nuxt />
      <no-ssr>
        <!-- <Footer /> -->
      </no-ssr>
    </div>
    <div v-else>
      <h1 style="text-align:center"> <strong>C A R G A N D O ...</strong> </h1>
      <div uk-spinner/>
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
</style>
