<template>
  <div 
    id="Services"
    :style="{'background-image':'url(' +imgSelected +')'}"
    class="uk-background-cover uk-flex uk-height-viewport">
    <div 
      class="uk-flex uk-flex-left uk-flex-middle"
      style="width: 40%">
      <div class="uk-padding-large">
        <p 
          class="text-style"
          style="color: white; width: 60%;display:block">
          {{ events.mainDescription }}
        </p>
        <div 
          v-if="events.events">
          <ul class="uk-nav">
            <li 
              v-for="(ele, key) in events.events"
              :key="key"
              style="padding: 10px 0">
              <div>
                <a 
                  :class="[selected==key? 'titleSelected':'']"
                  class="text-style"
                  style="color:#faeb05;font-weight: bold;text-decoration: none; padding-left: 20px;"
                  @click="getContent(key)">{{ ele.single.eventTitle }}</a>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </div>
    <!-- <hr 
      class="uk-divider-vertical" 
      style="width: 90%; border-left: 1px yellow solid"> -->
    <div 
      class="uk-flex uk-flex-column uk-flex-between"
      style="width:60%">
      
      <div 
        class="title uk-padding"
        style="padding-top: 200px; font-wei">
        <h2 
          v-if="events.events"
          style="color:white;font-weight: bold;"> {{ events.events[selected].single.eventImages[selected2].singleEvent.singleEventTitle }} </h2>
      </div>

      <div class="uk-padding-small">
        <div >
          <div 
            v-if="events.events"
            uk-slider>
            <ul 
              class="uk-slider-items uk-child-width-1-3@s uk-child-width-1-3@m">
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
      imgSelected:'foto1.png'
    }
  },
  mouted(){
    this.imgSelected = this.events.events[0].single.eventImages[0].singleEvent.singleEventImage
  },
  methods:{
    getContent(e){
      console.log(e)
      this.selected = e
      this.imgSelected = this.events.events[e].single.eventImages[0].singleEvent.singleEventImage
       this.selected2 = 0
      console.log(this.selected);
    },
    getImg(e,img){
      console.log(img.singleEvent.singleEventImage)
      this.selected2 = e
      this.imgSelected = img.singleEvent.singleEventImage
    }
  }
}
</script>

<style scoped>
  .text-style{
    font-size: 18px;
  }
  /* a:active { 
  background: url('/boton-1.png') no-repeat;
  background-size: cover;
  padding: 10px 15px;
  text-decoration: none;
} */
.titleSelected{
  background: url('/boton-1.png') no-repeat;
  z-index: -1;
  background-size:100%;
  text-align: left;
  font-weight: bold;
  color: #303e48 !important;
  padding: 25px 25px 25px 25px; 
}
.imgBorder{
  border: #faeb05 4px solid;
}

</style>
