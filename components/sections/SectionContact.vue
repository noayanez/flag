<template>
  <div
    id="Contact"
    class="uk-flex uk-flex uk-flex-center uk-flex-center uk-width-1-1"
    style="background-color: white; padding-left:10; min-height: 80vh;">
    <div class="uk-padding-small uk-flex uk-flex-column uk-flex-center uk-flex-middle uk-width-1-1">
      <div class="uk-width-2-3@m uk-width-4-5@s uk-width-1-1">
        <div
          class="title-text uk-text-bold uk-padding-small uk-text-center"
          style="color: black;">
          {{ contact.title }}
        </div>
        <div
          class="subitle-text uk-padding-small uk-text-center uk-padding-remove-vertical"
          style="color: black;">
          {{ contact.subtitle }}
        </div>
        <FormByColumns
          :form-content="contactForm"
          :btn-text="contact.btnText" />
      </div>
    </div>
  </div>
</template>

<script>
import FormByColumns from '~/components/general/FormByColumns.vue'
export default {
  components: {
    FormByColumns
  },
  props: {
    contactForm: {
      type: Array,
      default: null
    },
    contact: {
      type: Object,
      default: null
    }
  },
  data() {
    return {
      title: '¡CONTÁCTANOS!'
    }
  }
}
</script>

 <style lang="scss" scoped>
.title-text {
  font-size: 20px;
}
.subitle-text {
  font-size: 15px;
}
@media (min-width: 600px) {
  .title-text {
    font-size: 40px;
  }
  .subitle-text {
    font-size: 25px;
  }
}
 </style>
