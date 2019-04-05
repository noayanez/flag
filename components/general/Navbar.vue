<template>
  <div>
    <!-- Navbar for desktop -->
    <div
      uk-sticky="animation: uk-animation-slide-top; sel-target: .uk-navbar-container; cls-active: uk-navbar-sticky bkg-color; cls-inactive: uk-navbar-transparent uk-position-absolute uk-width-1-1; top: 80vh;"
      style="background-color: transparent;">
      <nav
        class=" uk-navbar-container uk-position-absolute uk-width-1-1  uk-navbar-center navStyle"
        style="z-index: 1000; height:80px"
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
                  style="max-width: 200px; height: 200px !important; padding-top: 63px;"
                  alt="Logo"></a>
            </div>
            <div
              v-else
              class="uk-navbar-item navItemStyle "
              style="">
              <a
                class="textElementsNav navBarStyle uk-position-relative"
                style="text-decoration:none"
                @click="goTo(`${section.url}`, `${section.name}`)"><span style="">{{ section.name }}</span></a>
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
          <div 
            v-for="(section, key) in sections"
            :key="key">
            <li
              v-if="section.name!=='logo'"
              style="justify-content:end !important;border-bottom: 1px solid white"
              class="uk-navbar-item navOffCanvasElementStyle">
              <a
                class="textElementsNav navOffCanvasTextStyle"
                @click="goTo(`${section.url}`, `${section.name}`)">{{ section.name }}</a>
            </li>
          </div>
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
  data(){
    return{
      sections:[
        {name:'EXPERIENCIAS MEMORABLES', url:'#Events'},
        {name:'MARKETING Y EVENTOS', url:'#Services'},
        {name:"logo", src:"/logo-principal.png"},
        {name:'¿POR QUÉ ELEGIRNOS?', url:'#Pilars'},
        {name:'CONTÁCTANOS', url:'#Contact'}
      ],
      logo:'logo-principal.png'
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

    }
  }
}
</script>

<style>
  .navStyle {
    
    background-color: transparent !important;
  }
  .bkg-color{
    background: rgba(0,0,0,0.5) !important;
  }

  .navBarStyle > span::after {
    transition: width 0.4s;
    position: absolute;
    height: 2px;
    width: 0%;
    left: 0;
    top: 110%;
    content: '';
    background-color: #faeb05;
  }
  .navBarStyle:hover > span::after {
    width: 100%;
}
  .navItemStyle {
    margin-right: 2em;
    white-space: normal !important;
  }

  .textElementsNav {
    font-family: 'Futura';
    font-weight: 700 !important;
    color: white !important;
    font-size: 16px;
    width: 70%;
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
  @media (min-width: 1367px) and  (max-width: 1601px){
    .textElementsNav{
      width: 95% !important;
    }
  }
  @media(max-width: 1366px){
    .textElementsNav {
      width: 94%;
  }
  }
</style>
