<template>
  <div id="Services">
    <div 
      :style="{'background-image':'url(' +imgSelected +')'}"
      class="uk-background-cover uk-flex uk-height-viewport uk-visible@s">
      <div 
        class="uk-flex uk-flex-left uk-padding-large uk-padding-remove-right uk-padding-remove-left uk-padding-remove-bottom "
        style="width: 40%">
        <div 
          class="uk-padding-large uk-padding-remove-right uk-padding-remove-top uk-padding-remove-bottom">
          <div style="border-right: 3px solid #faeb05; width:60%;">

            <p 
              class="text-style description"
              style="">
              {{ events.mainDescription }}
            </p>
            <div 
              v-if="events.events">
              <ul class="uk-nav">
                <li 
                  v-for="(ele, key) in events.events"
                  :key="key"
                  style="padding: 30px 0">
                  <a 
                    :class="[selected==key? 'title-color':'']"
                    class="text-style"
                    style="color:#faeb05;font-weight: bold;text-decoration: none; padding-left: 20px;"
                    @click="getContent(key)">
                    <div 
                      :class="[selected==key? 'titleSelected':'']"
                      style="width:50%;">{{ ele.single.eventTitle }}
                    </div>
                  </a>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div 
        class="uk-flex uk-flex-column uk-flex-between"
        style="width:60%">
      
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
                class="uk-slider-items uk-child-width-1-3@s ">
                <li 
                  v-for="(ele, key) in events.events[selected].single.eventImages"
                  :key="key">
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

    <!-- View mobile -->
    <div class="uk-hidden@s">
      <div 
        class="uk-padding"
        style="background-color:#101010">
        <div 
          v-if="events.events" 
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
          class=""
          style="color:white; text-align:center;">
          {{ events.mainDescription }}
        </p>
      </div>
      <div 
        v-if="events.events"
        uk-slideshow="animation: slide; autoplay: true; autoplay-interval: 4000; min-height: 300; max-height: 600">
        <div 
          class="uk-position-relative uk-visible-toggle uk-light" 
          tabindex="-1">
          <ul class="uk-slideshow-items">
            <li 
              v-for="(ele, key) in events.events[selected].single.eventImages"
              :key="key">
              <div 
                :style="`background-image: url(${ele.singleEvent.singleEventImage});`"
                style=""
                class="uk-height-1-1 uk-padding uk-align-center container-slider-events"/>
            </li>
          </ul>
          <a 
            class="uk-position-center-left uk-position-small uk-hidden-hover" 
            href="#" 
            uk-slidenav-previous 
            uk-slideshow-item="previous"/>
          <a 
            class="uk-position-center-right uk-position-small uk-hidden-hover" 
            href="#" 
            uk-slidenav-next 
            uk-slideshow-item="next"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

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
    }
  }
}
</script>

<style scoped>
  .text-style{
    font-size: 18px;
  }
.titleSelected{
  background: url('/boton-1.png') no-repeat;
  z-index: -1;
  background-size:cover;
  text-align: center;
  padding: 26px 5px 30px 2px;
}
.title-color{
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




@media (min-width: 768px) and (max-width: 1025px){
  .description{ 
    width: 100%;
}
.titleSelected{
        padding: 23px 21px 20px 23px;
}
}
@media (max-width: 468px){
  .select-style{
    display: block;
    font-size: 18px;
    padding: 1.5em 2em 1.5em 2.5em;
    background-color: yellow !important;
    border-radius: 6px;
    color: black;
    font-weight: bold;
    text-align-last: center;
}

}

</style>
