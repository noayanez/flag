<template>
  <div v-if= "downloaded">
    <SectionPortrait
      :portrait="portrait"
      :slide-nav="true"
      :arrow-slider="true"
    />
    <SectionUs
      :us="us"
    />
    <SectionProducts
      :products="products"
    />
    <!-- <SectionServices
      :services="services"
    /> -->
    <SectionCommentaries
      :commentaries="commentaries"
    />
    <SectionContact
      :contact-form="contactForm"
      :contact="contact"
    />
    <Footer
      :footer="footer"
    />
  </div>
  <div
    v-else
    class="uk-height-viewport uk-width-1-1 uk-flex uk-flex-center uk-flex-middle uk-font-bold uk-h1 uk-margin-remove loading-page">
    <!-- ADD HERE THE ANIMATION FOR LOADING -->
    <!-- DELETE THIS PART IF NOT NECESSARY -->
    CARGANDO ...
  </div>
</template>

<script>
import Vue from 'vue';
import VeeValidate,{ Validator } from 'vee-validate';
//DATA OF UBICATION FOR FORM COMPONENT
import depa from '@/data/departamentos.js'
import prov from '@/data/provincias.js'
import distri from '@/data/distritos.js'
// SECTION COMPONENTS
import SectionPortrait from '~/components/sections/SectionPortrait.vue'
import SectionUs from '~/components/sections/SectionUs.vue'
import SectionProducts from '~/components/sections/SectionProducts.vue'
// import SectionServices from '~/components/sections/SectionServices.vue'
import SectionCommentaries from '~/components/sections/SectionCommentaries.vue'
import SectionContact from '~/components/sections/SectionContact.vue'
import Footer from '~/components/general/Footer.vue'

// VALIDATOR FOR THE INPUTS IN THE FORM COMPONENT
Vue.use(VeeValidate);
const dictionary = {
  es: {
     messages:{
        required: (field) => `Por favor llene el campo ${field}`,
        email: () =>`Por favor ingrese un correo valido`,
        numeric: ()=>`Por favor ingrese solo numeros`
      }
  }
};
Validator.localize(dictionary);
const validator = new Validator({Nombre: 'required'})
validator.localize('es')

export default {
  components: {
    SectionPortrait,
    SectionUs,
    SectionProducts,
    // SectionServices,
    SectionCommentaries,
    SectionContact,
    Footer
  },
  data() {
    return {
      downloaded: true,
      portrait: '',
      us: '',
      products: '',
      services: '',
      commentaries: '',
      contact: '',
      footer: '',
      contactForm: [
        {
          items: [
            {
              name: 'Name',
              vmodel: '',
              type: 'input',
              format: 'text',
              placeholder: 'Nombre Completo'
            },
            {
              name: 'Email',
              vmodel: '',
              type: 'input',
              format: 'email',
              placeholder: 'Correo'
            },
            {
              name: 'Phone',
              vmodel: '',
              type: 'input',
              format: 'number',
              placeholder: 'Celular'
            }
          ]
        },
        {
          items: [
            {
              name: 'Need',
              vmodel: '',
              type: 'select',
              placeholder: '¿Qué servicio requieres?',
              options: [
                { value: 'Servicio1', text: 'Servicio 1' },
                { value: 'Servicio2', text: 'Servicio 2' },
                { value: 'Servicio3', text: 'Servicio 3' },
                { value: 'Servicio4', text: 'Servicio 4' },
                { value: 'Servicio5', text: 'Servicio 5' },
              ]
            },
            {
              name: 'Message',
              vmodel: '',
              type: 'text-area',
              format: 'text',
              placeholder: 'Cuéntanos sobre ti...',
            }
          ]
        }
      ]
    }
  },
  async mounted() {
    // HERE IS WHERE THE FETCHED INFORMATION IS DISTRIBUTED
    await this.$nextTick()
    try {
      let fetched = await this.$axios.$get('/site/page')
      // console.log(fetched)
      for (var i = 0; i < fetched.langs.length; i++) {
        if (fetched.langs[0].lang === 'es') {
          console.warn('CONTENIDO ACTUAL:')
          console.log(fetched.langs[i].content)
          this.portrait = fetched.langs[i].content.portrait
          this.us = fetched.langs[i].content.us
          this.products = fetched.langs[i].content.products
          this.services = fetched.langs[i].content.services
          this.commentaries = fetched.langs[i].content.commentaries
          this.contact = fetched.langs[i].content.contact
        }
      }
      let fetched2 = await this.$axios.$get('/site/settings')
      this.footer = fetched2
      console.warn('SETTINGS:')
      console.log(fetched2)
      // VERSION DE API-MULTILANGUAGE
      // console.log(fetched.content)
      // this.portrait = fetched.content.portrait
      // this.us = fetched.content.us
      // this.products = fetched.content.products
      // this.services = fetched.content.services
      this.downloaded = true
    } catch (e) {
      console.log('Errors')
    }
  },
  methods: {
    start(){
      this.downloaded = false
    },
    finish(){
      this.downloaded = true;
    }
  }
}
</script>

<style>
.loading-page {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(255, 255, 255, 0.8);
  text-align: center;
  padding-top: 200px;
  font-size: 30px;
  font-family: sans-serif;
}
</style>
