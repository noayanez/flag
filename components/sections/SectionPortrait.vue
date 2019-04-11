<template>
  <div 
    id="Portrait"
    class="uk-position-relative"
    style="min-height:100vh">
    <div
      :style="`background-image: url(${portrait.img};`"
      :class="device ? 'container-devices' : 'uk-height-viewport'"
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
      class="uk-position-center-left uk-text-left uk-padding-large uk-position-1-1 uk-width-1-1"
      style="color:#d5ecec;"> 
      <h1
        uk-slideshow-parallax="x: 100,-100"
        class="title-center uk-text-uppercase title-portrait"
        style="color:white; font-weight: bold;">
        {{ portrait.title }}
      </h1>
      <div 
        v-if="portrait.buttons"
        class="uk-height-1-1 buttons-conatiner"
        style="padding-top: 45px; display: flex; flex-wrap:wrap;">
        <a style="text-decoration:none; color:#314049;">
          <div class="button-portrait uk-text-uppercase">
            {{ portrait.buttons[0].btnText }}
          </div>
        </a>
        <a style="text-decoration:none; color:#314049;">
          <div class="button-portrait uk-text-uppercase">
            {{ portrait.buttons[1].btnText }}
          </div>
        </a>
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
  padding: 35px 46px 28px 45px;
  text-decoration: none;
  color: #303e48;
  font-size: 18px;
  font-family: 'Futura';
  font-weight: 800 !important;
}
.button-portrait:hover{
  background: url('/boton-2.png') no-repeat;
  background-size: 100%;
  padding: 35px 46px 28px 45px;
  color: #faeb05;
}
.title-portrait{
  width: 40%;
  padding-left: 20px;
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
@media (max-width: 420px){
  .button-portrait{
    margin-top: 10px;
}
.title-portrait{
  width: 90%;
  padding-left: 0px;
}
.button-portrait{
    padding: 40px 65px;
}
.button-portrait:hover{
  padding: 40px 65px;
}
.buttons-conatiner{
  justify-content: center;
}
.title-center{
      text-align: center;
}
.title-portrait{
    padding-top: 60px;
  }

}
</style>
