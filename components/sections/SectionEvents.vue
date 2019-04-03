<template>
  <div 
    id="Events"
    class="uk-animation-toggle"
  >
    <div 
      :style="{'background-image':'url(' +imgSelected +')'}"
      style="transition: opacity 5s ease-in;"
      class="uk-background-cover uk-flex uk-visible@m padding-events uk-height-viewport">
      <div 
        class="uk-flex uk-flex-left uk-padding-large uk-padding-remove-right uk-padding-remove-left uk-padding-remove-bottom width-col-1"
        style="">
        <div 
          class="uk-padding-large uk-padding-remove-right uk-padding-remove-top uk-padding-remove-bottom">
          <div class="container-into-col-1">
            <p 
              class="text-style description"
              style="">
              {{ events.mainDescription }}
            </p>
            <div 
              v-if="events.events">
              <ul 
                class="uk-nav"
                style="">
                <li 
                  v-for="(ele, key) in events.events"
                  :key="key"
                  style="padding: 20px 0px;">
                  <a
                    class="text-style"
                    style="color:#faeb05;font-weight: bold;text-decoration: none; padding-left: 20px;"
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
          class="title uk-padding-large"
          style="">
          <h2 
            v-if="events.events"
            style="color:white;font-weight: bold;"> {{ events.events[selected].single.eventImages[selected2].singleEvent.singleEventTitle }} </h2>
        </div>

        <div class="uk-width-1-1 uk-padding-small uk-padding-remove-left">
          <div >
            <div 
              v-if="events.events"
              uk-slider="finite: true; autoplay: true; autoplay-interval: 4000">
              <ul 
                class="uk-slider-items uk-child-width-1-3@s uk-child-width-1-4@l">
                <li 
                  v-for="(ele, key) in events.events[selected].single.eventImages"
                  :key="key"
                  class="padding">
                  <img 
                    :src="ele.singleEvent.singleEventImage"
                    :class="[selected2==key? 'imgBorder':'']"
                    style="border-radius: 20px; width: 250px;" 
                    alt="..."
                    @click="getImg(key,ele)">
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div 
      class="uk-hidden@m uk-height-viewport"
      style="display:flex; flex-direction:column">
      <div 
        class="uk-height-1-1"
        style="">
        <div 
          class="uk-padding height-component"
          style="background-color:#101010">
          <div 
            v-if="events.events"
            class="padding-select-left" 
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
          class="uk-height-1-1"
          uk-slideshow="animation: slide; autoplay: true; autoplay-interval: 3000; min-height: 350; max-height: 600">
          <div 
            class="uk-position-relative uk-visible-toggle uk-light" 
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
                  <div style="text-align:center"><h3>{{ events.events[selected].single.eventImages[selected2].singleEvent.singleEventTitle }}</h3></div>
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
      selected3:'',
      imgSelected:'foto1.png',
      select:''
    }
  },
  mouted(){
    this.loading()
  },
  methods:{
    getContent(e){
      console.log(e)
      console.log(this.selected3)
      this.selected = e
      this.imgSelected = this.events.events[e].single.eventImages[0].singleEvent.singleEventImage
       this.selected2 = 0
      console.log(this.selected);
    },
    getImg(e,img){
      console.log(img.singleEvent.singleEventImage)
      this.selected2 = e
      this.imgSelected = img.singleEvent.singleEventImage
    },
    loading(){
      this.imgSelected = this.events.events[0].single.eventImages[0].singleEvent.singleEventImage
      this.selected3 = this.events.events[0].single.eventTitle
      console.log(this.imgSelected)
    }
  }
}
</script>

<style scoped>
  @-webkit-keyframes fadeBackground { 
    0% { opacity: 0; }
    20% { opacity: 0; }
    40% { opacity: 0.3; }
    60% { opacity: 0.5; }
    80% { opacity: 0.9; }
    100% { opacity: 1; }
}
@keyframes fadeBackground { 
    0% { opacity: 0; }
    20% { opacity: 0; }
    40% { opacity: 0.3; }
    60% { opacity: 0.5; }
    80% { opacity: 0.9; }
    100% { opacity: 1; }
}

  .background-effect{
     display: block;
    -webkit-animation-name: fadeBackground;
    -webkit-animation-duration: 3s;
    animation-name: fadeIn;
    animation-duration: 3s;
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
    font-size: 16px;
  }
  .container-into-col-1{
    border-right: 3px solid #faeb05;
    width:60%;
  }
  .width-events{
    width:50%;
  }
  .padding-events{
    padding-bottom:40px;
  }
.titleSelected{
  background: url('/boton-1.png') no-repeat;
  z-index: -1;
  background-size:cover;
  text-align: center;
  padding: 26px 5px 30px 2px;
  font-weight: bold;
  color: #303e48 !important;
}
.imgBorder{
  border: #faeb05 4px solid;
}
.description{
  color: white; 
  width: 60%;
  display:block
}
.container-slider-events{
    background-size:cover; 
    background-position:50% 50%;
}
.width-col-1{
  width: 40%;
}
.width-col-2{
  width: 60%;
}



@media (min-width: 769px) and (max-width: 1025px){
  .titleSelected{
    padding: 25px 0px 32px 0px;
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
    width:75%;
  }
  .description{
    width: 90%;
}
  
}
@media (min-width: 469px) and (max-width: 768px){
  .description{ 
    width: 100%;
}
  .width-events{
    width:95%;
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

}
@media(min-width: 376px) and (max-width:417px){
  .padding-select-left{
    padding-left: 40px;
  }
  .ul-height{
    min-height: 440px !important;
  }
}
@media(min-width: 321px) and (width: 375px){
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

</style>
