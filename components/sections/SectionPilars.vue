<template >
  <section
    id="Pilars"
    class="uk-flex uk-flex-column uk-padding"
    style="background-color:black;">

    <div class="uk-padding-small">
      <div
        class="uk-h2 uk-margin-remove uk-text-bold uk-text-center uk-padding-small uk-text-uppercase"
        style="color:white">
        {{ pilars.pilarsSectionTitle }}
      </div>
      <div
        class="uk-h3 uk-margin-remove uk-text-bold uk-text-center uk-padding-small"
        style="color:white">
        {{ pilars.pilarsSectionSubtitle }}
      </div>
    </div>

    <div
      style="background-color:transparent;"
      class="uk-flex uk-flex-wrap uk-flex-center uk-margin-remove uk-visible@s">
      <!-- 80px = navbar size -->
      <div
        v-for="(section, key) in pilars.pilarsGroup"
        :key="key"
        class="uk-width-1-3@l uk-width-1-2@m uk-witdth-1-1 uk-padding-small">
        <div
          class="uk-padding-small"
          style="border-radius: 20px; color: black;">
          <div 
            :class="key==0?'duration1':key==1?'duration2':'duration3'"
            data-aos="fade-down"
            class="uk-flex uk-flex-column uk-flex-center uk-flex-middle uk-child-width-1-2 uk-child-width-1-1@s opacity-in">
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
// library for animate
import AOS from 'aos';
import 'aos/dist/aos.css';
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
      effect: false
    }
  },
  async mounted() {
    // Use it just when you want the effect depends on the first section after the portrait (100vh)
    // const html = document.querySelector('html')
    // window.addEventListener(
    //   'scroll',
    //   () => {
    //     if (html.scrollTop >= 2.2 * window.innerHeight) {
    //       console.log('entro');
    //       if (this.effect) return
    //       this.effect = true
    //     } else {
    //       this.effect = false
    //     }
    //   },
    //   false
    // )
    AOS.init();
  },
}
</script>

<style scoped>
  .duration1[data-v-e55b8b24]{
    transition-duration: 1200ms;
  }
  .duration2[data-v-e55b8b24]{
    transition-duration: 3200ms;
  }
  .duration3[data-v-e55b8b24]{
    transition-duration: 4200ms;
  }
  .opacity-in {
    opacity: 1;
    animation-name: fadeInOpacity;
    animation-iteration-count: 1;
    animation-timing-function: ease-in;
    animation-duration: 4.2s;
  }

@keyframes fadeInOpacity {
	0% {
		opacity: 0;
	}
  50%{
    opacity: 0.5;
  }
  75%{
    opacity: 0.75;
  }
	100% {
		opacity: 1;
	}
}

  .imageContainer{
    background-position:50% 50%;
    height: 160px;
    width: 160px;
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
    background-size:cover; 
    background-position:50% 50%; 
    height: 48vh;
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
