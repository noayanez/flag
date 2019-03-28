<template lang="html">
  <div class="uk-width-1-1 uk-padding-small">
    <div v-if="!submitted">
      <!-- HERE STARTS THE FORM -->
      <div 
        class="uk-flex uk-flex-wrap uk-width-1-1"
        style="">
        <div
          v-for="(column, key) in formContent"
          :key="key"
          class="uk-flex uk-flex-column uk-width-1-2@l uk-width-1-1">
          <div
            v-for="(item,i) in column.items"
            :key="i"
            :class="item.type==='text-area'?'uk-height-1-1':''"
            class="uk-width-1-1"
            style="padding: 0.5rem;">
            <input
              v-if="item.type==='input'"
              v-model="item.vmodel"
              :class="customClass"
              :style="'height: ' + (hInputs - 16) + 'px;' + customStyle"
              :placeholder="item.placeholder"
              :type="item.format"
              :pattern="item.patt">
            <select
              v-if="item.type === 'select'"
              v-model="item.vmodel"
              :class="customClass"
              :style="'height: 3rem;' + customStyle"
              required>
              <option
                value=""
                disabled
                selected>
                {{ item.placeholder }}
              </option>
              <option
                v-for="(option,j) in item.options"
                :key="j"
                :value="option.value">
                {{ option.text }}
              </option>
            </select>
            <textarea
              v-if="item.type === 'text-area'"
              v-model="item.vmodel"
              :class="customClass"
              :style="'height: ' + hTextArea + 'px;' + customStyle"
              :placeholder="item.placeholder"
              style="resize: none; padding-top: 0.7rem; padding-bottom: 0.7rem;"
            />
          </div>
        </div>
      </div>
      <div
        class="uk-width-1-1 uk-flex uk-flex-center uk-flex-middle uk-padding-small"
        style="outline: none;">
        <button
          :class="submitting ? 'pulse-btnd' : 'pulse-btnd'"
          @click="submitForm"
        >
          {{ submitting ? 'ENVIANDO...': btnText }}
        </button>
      </div>
      <!-- END OF THE FORM -->
    </div>
    <div v-else>
      {{ goToThanksPath() }}
    </div>
  </div>
</template>

<script>
export default {
  props: {
    // PROPS TO CREATE THE FORM
    formContent: {
      required: true,
      type: Array,
      default: null
    },
    btnText: {
      type: String,
      default: 'ENVIAR'
    }
  },
  data() {
    return {
      submitting: false,
      submitted: false,
      customClass: "uk-width-1-1",
      hTextArea: 0,
      hInputs: 64,
      customStyle: "padding-left: 1rem; padding-right: 1rem; color: black; border-radius: 5px; border: solid 2px; border-color: #e7153e; font-size: 20px; outline: none;"
    }
  },
  mounted() {
    var i = parseInt(this.formContent[0].items.length)
    var j = 0
    for (var x = 0; x < this.formContent[1].items.length; x++) {
      if (this.formContent[1].items[x].type === 'text-area') {
        break;
      }
      j++
    }
    this.hTextArea = ((i-j)*(this.hInputs))-16
  },
  methods: {
    async submitForm () {
      if (this.submitting) return
      try {
        var dataBody = {
          name: this.formContent[0].items[0].vmodel,
          email: this.formContent[0].items[1].vmodel,
          phone: this.formContent[0].items[2].vmodel,
          need: this.formContent[1].items[0].vmodel,
          message: this.formContent[1].items[1].vmodel
        }
        this.submitting = true
        console.log("DATA A ENVIAR")
        console.log(dataBody)
        const url = '/site/contact/form'
        console.log(url)
        await this.$axios.post(url, dataBody)
        this.submitted = true
      } catch (e) {
        window.alert('Ocurrió un error')
      } finally {
        this.submitting = false
      }

      // Send analytics data
      // if (!this.submitted || process.env.NODE_ENV !== 'production') return
      // try {
      //   if (window.fbq) window.fbq('track', 'CompleteRegistration')
      //   if (this.$ga) this.$ga.event('Formulario de contacto', 'Enviado', this.$route.path)
      // } catch (e) {
      //   console.log(e.message)
      // }
    },
    goToThanksPath () {
      var bodyNeed = ''
      var need = this.formContent[1].items[0].vmodel
      if (need === 'Servicio1'||
          need === 'Servicio2'||
          need === 'Servicio3'||
          need === 'Servicio4'||
          need === 'Servicio5') {
            bodyNeed = need
      } else {
        bodyNeed = 'default'
      }
      console.log(this.$store)
      this.$store.commit('setFromForm', true)
      console.log(this.$store.state.fromForm);
      if (this.$route.path === '/') {
        this.$router.push(this.$route.path + 'gracias/' + bodyNeed)
      } else {
        // THIS CASE OCCURS WHEN YOU COME FROM A CHILD PAGE NOT FROM THE MAIN (OR PORTRAIT)
        this.$router.push(this.$route.path + '/gracias/' + bodyNeed)
      }
    }
  }
}
</script>

<style lang="css">
.btn-send {
  color: black;
  background-color: white;
  border: solid 2px;
  border-color: black;
  padding: 0.5rem;
  font-size: 20px;
  border-radius: 5px;
  transition: all 0.5s ease;
  outline: none;
}
.btn-send:hover{
  transform: scale(1.1);
}

.pulse-btnd {
  outline: none;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 267.06px;
  height: 70px;
  font-size: 1.3em;
  font-family: Arial;
  text-transform: uppercase;
  text-align: center;
  color: white;
  border: none;
  text-decoration: none;
  color: white;
  border-radius: 12px;
  background: #ec2028;
  cursor: pointer;
  box-shadow: 0 0 0 0 rgba(#ec2028, 0.5);
  animation: pulsed 1.5s infinite;
}

.pulse-btnd:hover {
  animation: none
}

@keyframes pulsed {
  0% {
    transform: scale(0.9);
  }
  70% {
    transform: scale(1);
    box-shadow: 0 0 0 20px rgba(#ec2028, 0);
  }
  100% {
    transform: scale(0.9);
    box-shadow: 0 0 0 0 rgba(#ec2028, 0);
  }
}
</style>
