<template >
  <section
    id="Pilars"
    class="uk-flex uk-flex-column uk-padding"
    style="background-color:black;">

    <div class="uk-padding-small">
      <div
        class="uk-h2 uk-margin-remove uk-text-bold uk-text-center  uk-text-uppercase"
        style="color:white">
        {{ pilars.pilarsSectionTitle }}
      </div>
      <div
        class="uk-h3 uk-margin-remove uk-text-bold uk-text-center"
        style="color:white">
        {{ pilars.pilarsSectionSubtitle }}
      </div>
    </div>

    <div
      style="background-color:transparent;"
      uk-flex
      uk-scrollspy="cls: uk-animation-scale-down; target: > div > div > div; delay: 450; repeat: true"
      class="uk-flex uk-flex-wrap uk-flex-center uk-margin-remove uk-visible@s">
      <!-- 80px = navbar size -->
      <div
        v-for="(section, key) in pilars.pilarsGroup"
        :key="key"
        class="uk-width-1-3@l uk-width-1-2@m uk-witdth-1-1">
        <div
          class="uk-padding-small"
          style="border-radius: 20px; color: black;">
          <div 
            class="uk-flex uk-flex-column uk-flex-center uk-flex-middle uk-child-width-1-2 uk-child-width-1-1@s ">
            <div
              :style="`background-image: url(${section.singlePilar.singlePilarImage};`"
              style="background-size:cover; background-position: 50% 50%;"
              class="uk-height-1-1 uk-padding uk-align-center container-image"/>  
            <div   
              class="uk-width-4-5 uk-text-center">
              <div style="color:white">
                {{ section.singlePilar.singlePilarTitle }}
              </div>
              <div style="color:white; padding-top: 10px;width: 50%; margin:auto">
                {{ section.singlePilar.singlePilarDescription }}
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- View responsive -->
    <div 
      :class="device ? 'container-devices' : 'uk-height-viewport'"
      class="uk-hidden@s"
      style="">
      <div uk-slideshow="animation: slide; autoplay: true; autoplay-interval: 4000; min-height: 450; max-height: 600">
        <div 
          class="uk-position-relative uk-visible-toggle">
          <ul class="uk-slideshow-items">
            <li 
              v-for="(section, key) in pilars.pilarsGroup"
              :key="key">
              <div 
                :style="`background-image: url(${section.singlePilar.singlePilarImage};`"
                style=""
                class="uk-height-1-1 uk-padding uk-align-center container-slider"/>
              <div 
                class="uk-width-4-5 uk-text-center container-description">
                <div style="color:white">
                  {{ section.singlePilar.singlePilarTitle }}
                </div>
                <div
                  class="description" 
                  style="color:white; padding-top: 10px;">
                  {{ section.singlePilar.singlePilarDescription }}
                </div>
              </div>
            </li>
          </ul>
          <ul 
            class="uk-slideshow-nav uk-dotnav uk-flex-center"
            style="padding-bottom: 40px;"/>
        </div>
      </div>
    </div>
    
  </section>
</template>

<script>
export default {
  props:{
     pilars:{
      type: Object,
      default: function(){
        return{message: "Pilars"}
      }
    }
  },
  data(){
    return{ 
      effect: false,
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
    /* Permalink - use to edit and share this gradient: http://colorzilla.com/gradient-editor/#000000+0,000000+100&0.65+0,0+100;Neutral+Density */
    background: -moz-linear-gradient(top, rgba(0,0,0,0.65) 0%, rgba(0,0,0,0) 100%); /* FF3.6-15 */
    background: -webkit-linear-gradient(top, rgba(0,0,0,0.65) 0%,rgba(0,0,0,0) 100%); /* Chrome10-25,Safari5.1-6 */
    background: linear-gradient(to bottom, rgba(0,0,0,0.65) 0%,rgba(0,0,0,0) 100%); /* W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+ */
    filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#a6000000', endColorstr='#00000000',GradientType=0 ); /* IE6-9 */
  }
  .container-devices {
    height: 737px;
  }
  .imageContainer{
    background-position:50% 50%;
    height: 150px;
    width: 150px;
    border:4px solid #e41c43;
    background-color:#e41c43;
    background-size:75%;
  }

  .textStyle{
    padding-top: 2em;
  }

  .container-image{
    background-position:50% 50%;
    height: 160px;
    width: 160px;
    background-size:75%;
  }
  .container-slider{
    background-size:contain; 
    background-repeat: no-repeat;
    background-position:50% 50%; 
    width: 70%;
    border-radius: 30px;
}
.description{
    width: 50%; 
    margin:auto
}
@media (max-width: 420px){
    .description{
        width: 100%; 
        margin:auto
}
 .container-slider{
     width: 100%;
}
.container-description{
    margin:auto;
}
}

</style>
