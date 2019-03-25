<template lang="html">
  <div
    v-if="fromForm === true"
    class="uk-flex uk-flex-column uk-flex-center uk-flex-middle uk-width-1-1 uk-height-viewport"
    style="background-color: black; color: white;">
    <div
      v-if="actualPath !== 'default'"
      class="uk-flex uk-flex-column uk-flex-center uk-flex-middle">
      <div class="uk-padding">
        <div
          class="uk-padding"
          style="border: solid 2px; border-color: #59ec29; border-style: dashed;">
          <div class="">
            <p
              class="uk-text-center uk-text-bold uk-margin-remove"
              style="font-size: 50px;">
              GRACIAS
            </p>
            <p
              class="uk-text-center uk-margin-remove"
              style="font-size: 20px;">
              NOS CONTACTAREMOS PRONTO, ¡TEN UN BUEN DÍA!
            </p>
            <p
              class="uk-text-center uk-margin-remove"
              style="font-size: 20px;">
              QUE LA FUERZA ESTE CONTIGO.
            </p>
          </div>
        </div>
      </div>
    </div>
    <div
      v-else
      class="uk-flex uk-flex-column uk-flex-center uk-flex-middle">
      <p class="uk-text-large uk-text-bold">
        HOLA, CREO QUE NO DEBERIAS ESTAR AQUI
      </p>
    </div>
    <div class="p-3">
      <nuxt-link to="/">
        <button
          class="uk-text-bold"
          style="background-color: #59ec29; border-radius: 30px; border-color: transparent; font-size: 20px; letter-spacing: 0.08em; padding: 1rem; cursor: pointer;">
          Ir al inicio
        </button>
      </nuxt-link>
    </div>
  </div>
  <div
    v-else
    class="flex flex-col justify-center items-center bg-black w-full h-screen" />
</template>

<script>
// import M from '~/data/messages'
import { mapGetters } from 'vuex'
export default {
  data() {
    return {
      actualPath: '',
      fromForm: false
    }
  },
  computed: {
    ...mapGetters({
      // content: 'language/getAppContactForm
    })
  },
  mounted(){
    console.log(this.$store.state.fromForm)
    if (!this.$store.state.fromForm) {
      this.$router.push('/')
    } else {
      this.fromForm = true
      this.$store.commit('setFromForm',false)
    }
    this.actualPath = this.$route.params.slug
    console.log("PATH: " + this.$route.path)
  }
}
</script>

<style lang="css">
</style>
