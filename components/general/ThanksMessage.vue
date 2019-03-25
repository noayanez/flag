<template lang="html">
  <div class="flex flex-col justify-center items-center bg-black w-full h-screen">
    <!-- <h2 class="text-2xl sm:text-3xl md:text-4xl lg:text-5xl xl:text-6xl mb-3 tracking-wide p-3 text-white font-bold">
      {{ content.thanksmessage.subtitle }}
    </h2>
    <nuxt-link to="/">
      <button class="p-3 bg-green rounded-lg text-white font-bold">
        {{ content.btninicio }}
      </button>
    </nuxt-link> -->
  </div>
</template>

<script>
// import M from '~/data/messages'
import { mapGetters } from 'vuex'
export default {
  data() {
    return {
      actualPath : ''
    }
  },
  computed: {
    ...mapGetters({
      // content: 'language/getAppContactForm'
    })
  },
  mounted(){
    this.$router.push('/')
    this.actualPath = this.$route.params.slug
    console.log("PATH: " + this.$route.path)
  },
}
</script>

<style lang="css">
</style>
