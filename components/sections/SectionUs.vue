<template>
  <section
    id="Us"
    class="uk-flex uk-flex-column uk-flex-center uk-flex-middle uk-padding"
    style="background-color: pink; min-height: 100vh;">
    <div class="uk-width-1-1 uk-flex uk-flex-column uk-flex-center uk-flex-middle">
      <div
        class="title-text uk-text-bold uk-width-1-1 uk-text-center"
        style="color: black;">
        {{ us.title }}
      </div>
      <div class="uk-flex uk-flex-wrap uk-flex-center uk-flex-middle uk-child-width-1-2@m uk-child-width-1-1@m uk-width-1-1 uk-padding-remove-vertical">
        <div class="imageUs">
          <img
            :src="us.imageUrl"
            style="border-radius: 15px;">
        </div>
        <div class="uk-flex uk-flex-column uk-flex-middle">

          <div
            class="subtitle-text uk-padding-small uk-text-center uk-text-bold"
            style="color: black;">
            {{ us.subtitle }}
          </div>
          <div
            class="description-text uk-flex uk-flex-column uk-flex-middle uk-text-justify paddingUs"
            style="color: black;">
            {{ us.description }}
          </div>
          <div
            class="description-text boton-mochila margin-boton-mochila uk-flex uk-flex-center"
            style="">
            <a
              class="uk-text-bold pulse-btnd"
              @click="goTo(us.btnUrl)">
              {{ us.btnText }}
            </a>
          </div>

        </div>
      </div>
    </div>

  </section>
</template>

<script>
var UIkit

if (process.browser) {
  UIkit = require('uikit')
}

export default {
  props: {
    us: {
      type: Object,
      default: null
    }
  },
  data() {
    return {
    }
  },
  methods:{
    goTo (section) {
      UIkit.offcanvas('#offcanvas-nav-primary').hide().then(() => {
        //Validate screeen size
        UIkit.scroll({offset: 80}).scrollTo(section)
      })
    }
  }
}
</script>

<style scoped lang="scss">
.text-custom-bags {
  font-family: Arial !important;
  font-size: 45px !important;
  color: black
}
.button-red {
  background-color: #ec2028;
  color: white
}
.clip-palette2 {
  -webkit-clip-path: polygon(0 0, 52.5% 0, 47.5% 100%, 0% 100%);
  clip-path: polygon(0 0, 52.5% 0, 47.5% 100%, 0% 100%)
}
.scroll-shit::-webkit-scrollbar{
    width: .3rem
}
.scroll-shit::-webkit-scrollbar-thumb{
    background: #959595;
    border-radius: 10px;
    border: 1px solid #959595;
}
.scroll-shit::-webkit-scrollbar-track{
    background: white;
    border-radius: 10px;
}
@media (max-width: 400px) {
  .header-size2 {
    font-size: 18px !important
  }
  .content-size-letter2 {
    font-size: 15px !important
  }
  .margin-mochilas2 {
    margin-top: 30px !important
  }
}
@media (min-width: 401px) and (max-width: 800px) {
  .header-size2 {
    font-size: 20px !important
  }
  .content-size-letter2 {
    font-size: 16px !important
  }
  .margin-mochilas2 {
    margin-top: 30px !important
  }
  @media (min-width: 801px) {
    .margin-mochilas2 {
      margin-top: 40px !important
    }
  }
}
@media (max-width: 440px) {
  .myalv2 {
    padding-top: 45px !important;
    padding-bottom: 60px !important
  }
}
@media (min-width: 441px) and (max-width: 600px) {
  .myalv2 {
    padding-top: 45px !important;
    padding-bottom: 80px !important
  }
}
@media (min-width: 601px) and (max-width: 725px) {
  .myalv2 {
    padding-top: 45px !important;
    padding-bottom: 100px !important
  }
}
@media (min-width: 726px) and (max-width: 900px) {
  .myalv2 {
    padding-top: 45px !important;
    padding-bottom: 120px !important
  }
}
@media (min-width: 900px) and (max-width: 1199px) {
  .myalv2 {
    padding-top: 45px !important;
    padding-bottom: 160px !important
  }
}
@media (max-width: 1199px) {
  .fit-size {
    text-align: center !important;
    margin-top: 20px !important
  }
  .envio-size {
    width: 80% !important;
    text-align: center !important;
    margin: auto !important
  }
  .accesorio-size {
    width: 80% !important
  }
  .boton-mochila {
    display: flex;
    justify-content: center
  }
  .todo-size2 {
    width: 80% !important;
    margin: auto !important;
  }
  .alv-ancho2 {
    width: 100% !important
  }
}
@media (min-width: 1366px) and (max-width: 1600px) {
  .margin-boton-mochila {
    margin-top: 35px !important
  }
}
@media (min-width: 1601px) and (max-width: 1919px) {
  .margin-boton-mochila {
    margin-top: 28px !important
  }
}
@media (min-width: 1920px) {
  .margin-boton-mochila {
    margin-top: 20px !important
  }
}
@media (max-width: 1365px) {
  .margin-boton-mochila {
    margin-top: 30px !important
  }
}
input[type=number]::-webkit-inner-spin-button,
input[type=number]::-webkit-outer-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
.pulse-btnd {
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
.input-button {
  color: white;
  overflow: hidden;
  background: #ec2028;
  width: 30px;
  border: none;
  border-top-left-radius: 5px;
  border-bottom-left-radius: 5px;
  cursor: pointer
}
.input-button2 {
  color: white;
  overflow: hidden;
  width: 30px;
  background: #ec2028;
  border: none;
  border-top-right-radius: 5px;
  border-bottom-right-radius: 5px;
  cursor: pointer
}

.showButtonsBottom {
  display: none
}
@media (max-width: 1199px) {
  .showButtonsBottom {
      display: block !important;
  }
  .showButtonsBottom2 {
      display: none !important;
  }
}
.title-text {
  font-size: 30px;
  padding: 0.5rem;
}
.subtitle-text {
  font-size: 15px;
}
.description-text {
  font-size: 13px;
}
@media (min-width: 600px) {
  .title-text {
    font-size: 40px;
    padding: 2rem;
  }
  .subtitle-text {
    font-size: 25px;
  }
  .description-text {
    font-size: 20px;
  }
}
@media (min-width: 949px) {
  .imageUs {
    padding: 1rem;
  }
}
@media (min-width: 600px) {
  .paddingUs {
    padding-left: 1rem;
    padding-right: 1rem;
  }
}
</style>
