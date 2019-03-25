<template>
  <div id="Portrait">
    <div>
      <div
        class="uk-position-relative uk-visible-toggle "
        style=""
      >
        <ul
          class="uk-width-1-1"
          style="width:100%; heigth:100%;padding-left: 0px !important; margin-bottom:0px; ">
          <li 
            class="uk-height-1-1">
            <div class="uk-visible@s uk-height-1-1">
              <video 
                loop 
                muted 
                autoplay 
                style="width:100%; heigth:100% background-size:cover;  background-position:50% 50%;"
                class="video uk-height-1-1 uk-width-1-1 uk-height-1-1">
                <source 
                  src="/video1.mp4" 
                  type="video/mp4">
                Your browser does not support the video tag.
              </video>
            </div>
            <!-- <div
                  :style="'background-image: url(' + portrait.img +');'"
              style="background-size:cover;  background-position:50% 50%; width:100%; heigth:100%;"
              class="uk-height-viewport uk-height-1-1"/> -->
            <div
              style="background-image: url(fondo-negro.jpg);background-size:cover;background-position:50% 50%; width:100%; heigth:100%;"
              class="uk-height-viewport uk-height-1-1 uk-hidden@s"/> 
            <div
              class="uk-position-center-left uk-text-left uk-padding-large"
              style="color:#d5ecec">
              <h1
                uk-slideshow-parallax="x: 100,-100"
                style="color:white; font-weight: bold;">
                {{ portrait.title }}
              </h1>
              <div 
                v-if="portrait.buttons"
                style="padding-top: 45px; display: flex;">
                <div>
                  <a 
                    class="button-portrait">
                    {{ portrait.buttons[0].btnText }}
                  </a>
                </div>
                <div>
                  <a
                    class="button-portrait">
                    {{ portrait.buttons[1].btnText }}
                  </a>
                </div>
              </div>
            </div>
          </li>
        </ul>
        <!-- <div v-if="false">
          <a
            class="uk-position-center-left uk-position-small uk-hidden-hover"
            uk-slidenav-previous
            uk-slideshow-item="previous"/>
          <a
            class="uk-position-center-right uk-position-small uk-hidden-hover"
            uk-slidenav-next
            uk-slideshow-item="next"/>
        </div> -->
      </div>
      <div
        v-if="false"
        class="uk-position-bottom-center uk-position-small">
        <ul class="uk-slideshow-nav uk-dotnav uk-flex-center uk-margin"/>
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
      // portrait:{
      //   videoUrl:'https://youtu.be/VoGwvVoaoCw',
      //   title:'CREAMOS HISTORIAS DE ÉXITO',
      //   btn1:'EXPERIENCIA',
      //   btn2:'PRODUCTOS'

      // }
    }
  }
}
</script>

<style scoped>

.container-devices {
  height: 100vh
}
@media (max-width: 960px) {
  .container-devices {
    height: 690px !important
  }
}
.button-portrait{
  background: url('/boton-1.png') no-repeat;
  background-size: cover;
  padding: 35px 55px;
  text-decoration: none;
  color: #303e48;
  font-weight: bold;
}
@media (max-width: 420px){
  .button-portrait{
    background: url('/boton-1.png') no-repeat;
    background-size: cover;
    padding: 25px 30px;
    text-decoration: none;
    color: #303e48;
    font-weight: bold;
}
}
</style>
