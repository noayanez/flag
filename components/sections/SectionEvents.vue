<template>
  <div 
    id="Events"
   
    class="uk-position-relative"
    style="height:100vh">
    <div 
      v-if="events.events"
      
      class="uk-position-relative uk-visible@m uk-height-1-1">
      
      <div 
        v-for="(el, key) in events.events"
        :key="key"
        class="">
        <transition name="slide-fade">
          <div v-if="selected===key">
            <div 
              v-for="(ele, i) in events.events[selected].single.eventImages"
              :key="i">
              <div
                :style="{'background-image':'url(' +ele.singleEvent.singleEventImage +')'}"
                :class="(i)===selected2?'opacity-1':'opacity-0'"
                class="uk-background-cover uk-height-1-1 uk-flex uk-height-viewport padding-events transition-images uk-width-1-1 background-image "/>
            </div>
          </div>
        </transition>
      </div>
      <div 
     
        class="uk-flex uk-visible@m  uk-height-1-1 padding-events transition-images uk-width-1-1  background-image gradient">
        <div 
          class="uk-padding-large uk-padding-remove-right uk-padding-remove-left uk-padding-remove-bottom width-col-1"
          style="">
          <div 
            class="uk-flex uk-flex-column uk-flex-center uk-padding-large uk-padding-remove-right uk-padding-remove-top uk-padding-remove-bottom uk-height-1-1">
            <div class="container-into-col-1 uk-height-1-1">
              <div
                class="uk-flex uk-flex-column uk-flex-center" 
                style="height:30%;">
                <div>
                  <p 
                    class="text-style description uk-margin-remove">
                    {{ events.mainDescription }}
                  </p>
                </div>
              </div>
              <div 
                v-if="events.events"
                uk-height-viewport="expand: true"
                style="height:70%">
                <ul 
                  class="uk-nav uk-flex uk-flex-column uk-flex-around uk-flex-top"
                  style="height:100%">
                  <li 
                    v-for="(ele, key) in events.events"
                    :key="key"
                    class=""
                    style="">
                    <a
                      class="text-style"
                      style="color:#faeb05;font-weight: bold;text-decoration: none;display: inline-block"
                      @click="getContent(key)">
                      <div 
                        :class="[selected==key? 'titleSelected':'']"
                        class="width-events"
                        style="">{{ ele.single.eventTitle }}
                      </div>
                    </a>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
        <div 
          class="uk-flex uk-flex-column uk-flex-between width-col-2"
          style="">
          
          <div 
            class="uk-flex uk-flex-column uk-flex-center"
            style="height:37%">
            <div>
              <h2 
                v-if="events.events"
                style="color:white;font-weight: bold;"> {{ events.events[selected].single.eventImages[selected2].singleEvent.singleEventTitle }} </h2>
            </div>
          </div>

          <div 
            class="uk-flex uk-width-1-1 uk-padding-small"
            style="width:90%">
            <div >
              <div 
                v-if="events.events"
                uk-slider="finite: true; autoplay: true; autoplay-interval: 4000; min-height: 450px;">
                <ul 
                  style=""
                  class="uk-slider-items uk-child-width-1-4@m uk-child-width-1-4@l uk-grid">
                  <li 
                    v-for="(ele, key) in events.events[selected].single.eventImages"
                    :key="key"
                    class=""
                    style="">
                    <img 
                      :src="ele.singleEvent.singleEventImage"
                      :class="[selected2==key? 'imgBorder':'']"
                      style="border-radius: 20px; width: 400px;" 
                      alt="..."
                      @click="getImg(key,ele)">
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div 
      
      class="uk-hidden@m"
      style="display:flex; flex-direction:column; height:100%">
      <div 
        class="uk-height-1-1"
        style="">
        <div 
          class="uk-flex uk-flex-column uk-flex-center uk-flex-middle height-col-1"
          style="background-color:#101010;">
          <div 
            v-if="events.events"
            class="" 
            style="text-align:center">
            <select
              v-model="selected"
              class="select-style">
              <option 
                v-for="(ele, key) in events.events"
                :key="key"
                :value="key">{{ ele.single.eventTitle }}</option>
            </select>
          </div>
          <p 
            class="description-style"
            style="">
            {{ events.mainDescription }}
          </p>
        </div>
        <div 
          v-if="events.events"
          class="uk-height-1-1 height-col-2"
          uk-slideshow="animation: slide; autoplay: true; autoplay-interval: 3000; min-height: 350; max-height: 600">
          <div 
            class="uk-position-relative uk-visible-toggle uk-light uk-height-1-1" 
            tabindex="-1">
            <ul class="uk-slideshow-items uk-height-1-1 ul-height">
              <li 
                v-for="(ele, key) in events.events[selected].single.eventImages"
                :key="key"
                style="uk-height-1-1">
                <div 
                  :style="`background-image: url(${ele.singleEvent.singleEventImage});`"
                  style="background-size:cover; background-position: 50% 50%"
                  class="uk-height-1-1 uk-padding uk-align-center container-slider-events ">
                  <div style="text-align:center; padding:0px"><h3>{{ events.events[selected].single.eventImages[selected2].singleEvent.singleEventTitle }}</h3></div>
                </div>
              </li>
            </ul>
            <a 
              class="uk-position-center-left uk-position-small"
              style="padding-left:4%"
              href="#" 
              uk-slideshow-item="previous">
              <svg 
                width="35px" 
                height="35px" 
                viewBox="0 0 25 40" 
                xmlns="http://www.w3.org/2000/svg">
                <polyline 
                  fill="none" 
                  stroke="#faeb05" 
                  stroke-width="2" 
                  points="20.527,1.5 2,20.024 20.525,38.547 "/>
              </svg>
            </a>
            <a 
              class="uk-position-center-right uk-position-small" 
              style="padding-right:4%"
              href="#" 
              uk-slideshow-item="next">
              <svg 
                width="35px" 
                height="35px" 
                viewBox="0 0 25 40" 
                xmlns="http://www.w3.org/2000/svg">
                <polyline 
                  fill="none" 
                  stroke="#faeb05" 
                  stroke-width="2" 
                  points="4.002,38.547 22.527,20.024 4,1.5 "/>
              </svg>
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script scoped>

export default {
  props: {
    events: {
      type: Object,
      default: function() {
        return {message: "events"}
      }
    }
  },
  data(){
    return{
      services:{},
      selected:0,
      selected2:0,
      selected3:false,
      imgSelected:'',
      select:'',
      device:''
    }
  },
  mounted(){
    // console.log(window.innerHeight)
    // console.log(window.innerWidth)
    this.loading()
    var userAgent = navigator.userAgent || navigator.vendor || window.opera
      if (/iPad|iPhone|iPod/.test(userAgent) && !window.MSStream) {
        this.device = true
    }
  },
  methods:{
    getContent(e){
      this.selected = e
      this.selected2 = 0
      this.selected3 = true
      console.log("selected: " + this.selected);
    },
    getImg(e,img){
      console.log("key selected2:" + e)
      this.selected2 = e
    },
    loading(){
      // this.imgSelected = this.events.events[0].single.eventImages[0].singleEvent.singleEventImage
      // this.selected3 = this.events.events[0].single.eventTitle
    }
  }
}
</script>

<style>
  .gradient {
    /* Permalink - use to edit and share this gradient: http://colorzilla.com/gradient-editor/#000000+0,000000+100&0.65+0,0+100;Neutral+Density */
    background: -moz-linear-gradient(top, rgba(0,0,0,0.65) 0%, rgba(0,0,0,0) 100%); /* FF3.6-15 */
    background: -webkit-linear-gradient(top, rgba(0,0,0,0.65) 0%,rgba(0,0,0,0) 100%); /* Chrome10-25,Safari5.1-6 */
    background: linear-gradient(to bottom, rgba(0,0,0,0.65) 0%,rgba(0,0,0,0) 100%); /* W3C, IE10+, FF16+, Chrome26+, Opera12+, Safari7+ */
    filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#a6000000', endColorstr='#00000000',GradientType=0 ); /* IE6-9 */
  }
  .slide-fade-enter-active {
  transition: all 1s ease;
  }
  .slide-fade-leave-active {
  transition: all 1s ease;
  }
  .slide-fade-leave, .slide-fade-leave-active {
  opacity: 1;
  }
  .slide-fade-enter, .slide-fade-leave-active {
  opacity: 0;
  }
  .container-devices-services {
     height: 800px;
  }
  .opacity-0{
    opacity: 0;
  }
  .opacity-1{
    opacity: 1;
  }
  @keyframes animal {
    0%{
      opacity: 0;
      transform: scale(0);
    }
    100%{
       opacity: 1;
      transform: scale(1);
    }
    
  }
  .transition-images{
    position:absolute;
    -webkit-transition: opacity  1.5s ease-in-out;
    -moz-transition: opacity 1.5s ease-in-out;
    -o-transition: opacity  1.5s ease-in-out;
    transition: opacity 1.5s ease-in-out;
}
.transition-list{
    animation: animal ease-in-out 2s forwards;
}
.background-image::after {
  content:"";
  position:absolute;
  top:0;
  left:0;
  width:100%;
  height:100%;
  background:rgba(0,0,0,0);
  z-index:-1;
}
.height-col-1{
  height: 25%;
}
.height-col-2{
  height: 75%;
}
  
.select-style{
  display: block;
  font-size: 18px;
  padding: 1.5em 2em 1.5em 1.5em;
  background-color: #faeb05 !important;
  border-radius: 6px;
  color: black;
  font-weight: bold;
  text-align-last: center;
}
.description-style{
  color:white; 
  text-align:center;
  font-size:20px;
}


  .text-style{
    font-size: 18px;
  }
  .container-into-col-1{
    border-right: 3px solid #faeb05;
    width:90%;
  }
  .width-events{
    width:100%;
  }
  .padding-events{
    padding-bottom:40px;
  }
.titleSelected{
  background: url('/boton-1.png');
  background-repeat: no-repeat;
  background-size: 100% 95%;
  background-position: 50% 50%;
  padding: 36px 7px 30px 36px;
  color: #303e48 !important;
}
.imgBorder{
  border: #faeb05 3.5px solid;
}
.description{
  color: white; 
  width: 93%;
  display:block;
  font-size: 20px;
}
.container-slider-events{
    background-size:cover; 
    background-position:50% 50%;
}
.width-col-1{
  width: 30%;
}
.width-col-2{
  width: 70%;
}

@media (min-width: 1369px) and (max-width: 1601px){
  .padding-li {
    padding: 15px 0px 15px 7px;
  }
  .text-style {
    font-size: 18px;
  }
  .description{
    font-size: 24px;
  }
}
.padding-li{
  padding: 25px 0px 25px 7px;
}

@media (min-width: 769px) and (max-width: 1366px){
  .titleSelected{
    padding: 25px 7px 24px 23px;
}
  .width-col-1{
    width: 30%;
}
  .width-col-2{
    width: 70%;
}
  .container-into-col-1{
    width:100%;
  }
  .padding{
    padding: 10px;
  }
  .width-events{
    width:100%;
  }
  .description{
    width: 90%;
  }
  .text-style{
    font-size: 17px;
  }
  .padding-li{
    padding: 15px 0px 15px 7px;
  }
}
@media (min-width: 469px) and (max-width: 768px){
  .description{ 
    width: 100%;
}
  .width-events{
    width:100%;
  }
  .container-into-col-1{
    width:75%;
  }
  .ul-height{
    min-height: 659px !important;
  }
  .height-component{
    padding-top: 110px;
  }
  .description-style{
    font-size:24px;
  }
  .select-style{
    margin: auto;
  }
  .text-style{
    font-size: 17px;
  }
}
@media (max-width: 468px){
  .select-style{
    display: block;
    font-size: 18px;
    padding: 1.5em 2em 1.5em 1.5em;
    background-color: #faeb05 !important;
    border-radius: 6px;
    color: black;
    font-weight: bold;
    text-align-last: center;
}
.text-style{
    font-size: 17px;
  }
  .height-col-1{
  height: 45%;
}
.height-col-2{
  height: 55%;
}
.description-style{
  padding-top: 10px;
}

}
@media(min-width: 376px) and (max-width:417px){
  .padding-select-left{
    padding-left: 40px;
  }
  .ul-height{
    min-height: 440px !important;
  }
}
@media(min-width: 321px) and (max-width: 375px){
  .padding-select-left{
    padding-left: 26px;
  }
  .ul-height{
    min-height: 530px !important;
  }
}
@media (max-width: 320px){
  .select-style{
       padding: 1.5em 0em 1.5em 1.5em;
}

}
.uk-nav > li > a {
    padding: 0px 0;
}


</style>
