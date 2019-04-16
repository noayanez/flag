<template>
  <div
    id="Portrait"
    class="uk-position-relative height-portrait">
    <div
      :style="`background-image: url(${portrait.img};`"
      style="background-size:cover;background-position:50% 50%; width:100%;"
      class="uk-height-1-1 uk-hidden@s uk-position-absolute"/>
    <div class="uk-visible@s uk-height-1-1">
      <video
        loop
        muted
        autoplay
        style="width:100%; heigth:100% background-size:cover;  background-position:50% 50%;"
        class="video uk-height-1-1 uk-width-1-1 uk-height-1-1 uk-video">
        <source
          src="/video1.mp4"
          type="video/mp4">
        Your browser does not support the video tag.
      </video>
    </div>
    <div
      class="gradient uk-width-1-1"
      style="position: absolute; height: 100%;top:0;"/>
    <div
      class="uk-position-center-left uk-text-left uk-padding-large uk-position-1-1 uk-width-1-1"
      style="color:#d5ecec;">
      <h1
        uk-slideshow-parallax="x: 100,-100"
        class="uk-width-1-2@s uk-width-1-1 title-center uk-text-center uk-text-left@s uk-text-uppercase title-portrait"
        style="color:white; font-weight: bold;">
        {{ portrait.title }}
      </h1>
      <div
        v-if="portrait.buttons"
        class="uk-height-1-1 uk-flex uk-flex-wrap"
        style="padding-top: 45px;">
        <div class="uk-width-auto@s uk-width-1-1 uk-flex uk-flex-left@s uk-flex-center uk-flex-middle">
          <a
            style="text-decoration: none;color:#314049; margin-bottom: 10px;"
            @click="goTo('#Events')">
            <div
              class="button-portrait uk-text-uppercase uk-flex uk-flex-center uk-flex-middle uk-text-center"
              style="outline: none;">
              {{ portrait.buttons[0].btnText }}
            </div>
          </a>
        </div>
        <div class="uk-width-auto@s uk-width-1-1  uk-flex uk-flex-left@s uk-flex-center uk-flex-middle">
          <a
            style="text-decoration: none;color:#314049; margin-bottom: 10px;"
            @click="goTo('#Services')">
            <div
              class="button-portrait uk-text-uppercase uk-flex uk-flex-center uk-flex-middle uk-text-center"
              style="outline: none;">
              {{ portrait.buttons[1].btnText }}
            </div>
          </a>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
/**
 * images       = path de imagenes a mostrar
 * arrowSlider  = true para mostrar flechas false para ocultarlos
 * slideNav     = para mostrar para mostrar los botones de navegación
 */
var UIkit

if (process.browser) {
  UIkit = require('uikit')
}
export default {
  props: {
    portrait: {
      type: Object,
      default: function() {
        return {message: "rutas de imagenes"}
      }
    },
    slideNav: {
      type: Boolean,
      default: function() {
        return {message: "opcional"}
      }
    },
    arrowSlider:{
      type: Boolean,
      default: function(){
        return {message: "Flechas slider"}
      }
    },
    content:{
      type: Object,
      default: function(){
        return{message: "message slider"}
      }
    }
  },
  data(){
    return{
      device:''
    }
  },
   mounted(){
     var userAgent = navigator.userAgent || navigator.vendor || window.opera
    if (/iPad|iPhone|iPod/.test(userAgent) && !window.MSStream) {
      this.device = true
    }
  },
  methods: {
    goTo (section, label) {
      UIkit.offcanvas('#offcanvas-nav-primary').hide().then(() => {
        //Validate screeen size
        UIkit.scroll({offset: 0}).scrollTo(section)
      })
    }
  }
}
</script>

<style scoped>
.gradient {
    /* Permalink - use to edit and share this gradient: http://colorzilla.com/gradient-editor/#000000+0,000000+100&0.65+0,0.71+100;Neutral+Density */
background: -moz-linear-gradient(top, rgba(0,0,0,0.65) 0%, rgba(0,0,0,0.71) 100%); /* FF3.6-15 */
background: -webkit-linear-gradient(top, rgba(0,0,0,0.65) 0%,rgba(0,0,0,0.71) 100%); /* Chrome10-25,Safari5.1-6 */
background: linear-gradient(to bottom, rgba(0,0,0,0.65) 0%,rgba(0,0,0,0.71) 100%); /* W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+ */
filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#a6000000', endColorstr='#b5000000',GradientType=0 ); /* IE6-9 */
  }
.container-devices {
  height: 737px;
}
.button-portrait{
  background: url('/boton-1.png') no-repeat;
  background-size: 100%;
  text-decoration: none;
  color: #303e48;
  font-size: 18px;
  width: 200px;
  height: 90px;
  font-family: 'Futura';
  font-weight: 800 !important;
  transition: all 0.5s ease;
}
.button-portrait:hover{
  background: url('/boton-2.png') no-repeat;
  background-size: 100%;
  width: 200px;
  height: 90px;
  color: #faeb05;
}
.title-portrait{
  padding-left: 20px;
  padding-right: 20px;
  font-family: 'Futura';
  font-weight: 800 !important;
}
@media (max-width: 960px) {
  .title-portrait{
    margin-bottom: 0px;
    font-size: 2rem;
  }
  .logo-style{
    position: absolute;
    top: 0;
    left: 76px;
  }
}
@media(max-width: 640px){
  .height-portrait{
    min-height:100vh;
  }
}
@media (max-width: 420px){
  .button-portrait{
    margin-top: 10px;
  }
  .title-portrait{
    padding-left: 0px;
  }
  .title-center{
    text-align: center;
  }
  .title-portrait{
    padding-top: 60px;
  }
}
</style>
