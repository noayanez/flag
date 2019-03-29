<template>
  <div>
    <!-- Navbar for desktop -->
    <div
      uk-sticky="animation: uk-animation-slide-top; sel-target: .uk-navbar-container; cls-active: uk-navbar-sticky; cls-inactive: uk-navbar-transparent uk-position-absolute uk-width-1-1; top: 80vh;"
      style="background-color: transparent;">
      <nav
        class=" uk-navbar-container uk-position-absolute uk-width-1-1  uk-navbar-center navStyle"
        style="z-index: 1000; height:120px"
        uk-navbar>
        <div class="uk-navbar-center uk-visible@l">
          <div 
            v-for="(section, key) in sections"
            :key="key">
            <div 
              v-if="section.name=='logo'"
              class="uk-navbar-item navItemStyle"
              style="width: 120px; height:90px;">
              <a
                class="uk-navbar-item uk-logo"
                @click="goTo('#Portrait')">
                <img
                  :src="section.src"
                  width="150px"
                  style="max-width: 200px; height: 200px !important; padding-top: 50px;"
                  alt="Logo"></a>
            </div>
            <div
              v-else
              class="uk-navbar-item navItemStyle">
              <a
                :class="[active == key ? 'subrayado':'leave']"
                class="textElementsNav"
                style="text-decoration:none"
                @mouseover="overMouse(key)"
                @mouseleave="leaveMouse()"
                @click="goTo(`${section.url}`, `${section.name}`)">{{ section.name }}</a>
            </div>

          </div>
        </div>
        <div
          class="uk-navbar-right uk-hidden@l">
          <a
            class="uk-navbar-toggle"
            uk-navbar-toggle-icon
            uk-toggle="target: #offcanvas-nav-primary"
            style="color:white !important"
            href="#offcanvas-nav-primary"/>
        </div>
      </nav>
    </div>

    <div
      id="offcanvas-nav-primary"
      class="uk-hidden@l"
      uk-offcanvas="flip:true overlay: true">
      <div class="uk-offcanvas-bar uk-flex uk-flex-column">
        <a
          class="uk-navbar-toggle"
          uk-navbar-toggle-icon
          uk-toggle="target: #offcanvas-nav-primary"
          style="color:white !important; justify-content:flex-end !important;"/>
        <ul class="uk-nav uk-nav-primary uk-nav-center">
          <li
            v-for="(section, key) in sections"
            :key="key"
            style="justify-content:end !important;"
            class="uk-navbar-item navOffCanvasElementStyle">
            <a
              class="textElementsNav navOffCanvasTextStyle"
              @click="goTo(`${section.url}`, `${section.name}`)">{{ section.name }}</a>
          </li>
        </ul>
      </div>
    </div>


  </div>
</template>

<script>

var UIkit

if (process.browser) {
  UIkit = require('uikit')
}

export default {
  // props:{
  //   logo:{
  //     type:String,
  //     default: function(){
  //       return{message:"hola hola logo"}
  //     }
  //   }
  // },
  data(){
    return{
      sections:[
        {name:'EXPERIENCIAS MEMORABLES', url:'#Events'},
        {name:'MARKETING Y EVENTOS', url:'#Services'},
        {name:"logo", src:"/logo-principal.png"},
        {name:'¿POR QUÉ ELEGIRNOS?', url:'#Pilars'},
        {name:'CONTÁCTANOS', url:'#Contact'}
      ],
      logo:'logo-principal.png',
      active:''
    }
  },
  methods: {
    goTo (section, label) {

      UIkit.offcanvas('#offcanvas-nav-primary').hide().then(() => {
        //Validate screeen size
        UIkit.scroll({offset: 80}).scrollTo(section)
      })

      // if (window.outerWidth > 960){
      //   UIkit.offcanvas('#offcanvas-nav-primary').hide().then(() => {
      //   //Validate screeen size
      //     UIkit.scroll({offset: 80}).scrollTo(section)
      //   })
      // }
      // else{
      //   UIkit.offcanvas('#offcanvas-nav-primary').hide().then(() => {
      //   //Validate screeen size
      //     UIkit.scroll({offset: 0}).scrollTo(section)
      //   })
      // }

    },
    overMouse(key){
        this.active = key
      },
      leaveMouse(){
        this.active = null
        console.log(this.active);
        
      }
  }
}
</script>

<style>
  .navStyle {
    /* background: rgba(0,0,0,0.5) !important; */
    background-color: transparent !important;
  }
   /* .subrayado{
     position: absolute;
     z-index: -1;
     transform: translateX(-60px);
     border-bottom: 2px solid black;
} */
  /* a.textElementsNav{
    transition: all .35s ease-in-out;
  } */
  .leave{
    border:none
  }

  .navItemStyle {
    margin-right: 1em;
  }

  .textElementsNav {
    font-weight: bolder;
    color: white !important;
    font-size: 17.5px;
  }
  .navOffCanvasElementStyle {
    padding: 1em;
    min-height: 0px !important;
  }
  .navOffCanvasTextStyle {
    color:cadetblue !important;
    font-size: 12px !important;
    text-transform: uppercase;
    min-height: 0px !important;
  }
  .uk-sticky-placeholder{
    height: 0px;
  }
</style>
