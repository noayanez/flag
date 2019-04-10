<template>
  <div>
    <SectionPortrait
      :portrait="portrait"
      :slide-nav="true"
      :arrow-slider="true"
    />
    <SectionEvents
      :events="events"
    />
    <SectionServices
      :services="services"
    />
    <SectionPilars
      :pilars="pilars"/>
    <SectionContact
      :footer="footer"
    />
  </div>
</template>

<script>


import { mapGetters} from 'vuex'


import Vue from 'vue';
import VeeValidate,{ Validator } from 'vee-validate';

// SECTION COMPONENTS
import SectionPortrait from '~/components/sections/SectionPortrait.vue'
import SectionEvents from '~/components/sections/SectionEvents.vue'
import SectionContact from '~/components/sections/SectionContact.vue'
import SectionServices from '~/components/sections/SectionServices.vue'
import SectionPilars from '~/components/sections/SectionPilars.vue'

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
    SectionEvents,
    SectionContact,
    SectionServices,
    SectionPilars
  },
  data() {
    return {
      portrait: {},
      events:{},
      footer: {},
      services:{},
      pilars:{},
      contact:{}
    }
  },
   computed: {
    ...mapGetters({
        content: 'getView'    
    }),
    ...mapGetters({
        content2: 'getInfoGeneral'    
    })
},
  async mounted() {
    // HERE IS WHERE THE FETCHED INFORMATION IS DISTRIBUTED
    await wait(1000)
     this.portrait = this.content.content.portrait
     this.events = this.content.content.eventsSection
     this.services = this.content.content.services
     this.pilars =  this.content.content.pilars
     this.footer =  this.content2
    console.log( this.footer )
    var intFrameHeight = window.innerHeight;
  },
  methods: {
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
