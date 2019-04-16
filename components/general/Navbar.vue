<template>
  <div>
    <!-- Navbar for desktop -->
    <div
      uk-sticky="animation: uk-animation-slide-top; sel-target: .uk-navbar-container; cls-active: uk-navbar-sticky bkg-color; cls-inactive: uk-navbar-transparent uk-position-absolute uk-width-1-1; top: 80vh;"
      style="background-color: transparent;">
      <nav
        class=" uk-navbar-container uk-position-absolute uk-width-1-1  uk-navbar-center navStyle"
        style="z-index: 1000; height: 70px"
        uk-navbar>
        <div
          class="uk-navbar-center uk-visible@l uk-height-1-1 uk-flex uk-flex-around uk-flex-middle"
          style="width: 90%;">
          <div
            v-for="(section, key) in sections"
            :key="key"
            class="uk-height-1-1"
            style="width: 15%">
            <div
              v-if="section.name=='logo'"
              class="uk-navbar-item uk-width-1-1 uk-height-1-1 uk-flex uk-flex-around uk-flex-middle"
              style="padding: 0 !important; background: transparent; margin-left: 1rem; margin-right: 1rem;">
              <a
                class="uk-navbar-item uk-logo"
                style="padding: 0 0 0 0 !important;"
                @click="goTo('#Portrait')">
                <img
                  id="logoHome"
                  width="150px"
                  style="max-width: 200px; height: 169px !important; padding-top: 50px;"></a>
            </div>
            <div
              v-else
              class="uk-navbar-item uk-width-1-1 uk-height-1-1 uk-text-center"
              style="padding: 0 !important; background: transparent; margin-left: 1rem; margin-right: 1rem;">
              <div class="uk-width-1-1 navBarStyle">
                <a
                  class="textElementsNav uk-position-relative uk-width-1-1 uk-flex uk-flex-center uk-flex-middle"
                  style="text-decoration:none"
                  @click="goTo(`${section.url}`, `${section.name}`)">
                  <p class="uk-width-1-1 uk-margin-remove">{{ section.name }}</p>
                </a>
              </div>
            </div>

          </div>
        </div>
        <div
          class="uk-navbar-right uk-hidden@l">
          <a
            class="uk-navbar-toggle"
            uk-navbar-toggle-icon
            uk-toggle="target: #offcanvas-nav-primary"
            style="color:white !important; height: 70px;"
            href="#offcanvas-nav-primary"/>
        </div>
      </nav>
    </div>

    <div
      id="offcanvas-nav-primary"
      class="uk-hidden@l"
      uk-offcanvas="flip:true overlay: true">
      <div class="uk-offcanvas-bar uk-flex uk-flex-column uk-flex-between">
        <div
          class="uk-width-1-1"
          style="">
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
                style="justify-content:end !important;border-bottom: 1px solid white; "
                class="uk-navbar-item navOffCanvasElementStyle">
                <a
                  class="textElementsNav navOffCanvasTextStyle"
                  style=""
                  @click="goTo(`${section.url}`, `${section.name}`)">
                  {{ section.name }}
                </a>
              </li>
            </div>
          </ul>
        </div>
        <div>
          <div
            class="uk-width-1-1 uk-flex uk-flex-center uk-flex-middle"
            style="">
            <a
              href=""
              style="margin: 10px; cursor: pointer; border-radius: 999px">
              <img
                src="/facebook.png"
                style="border-radius: 999px"
                width="40">
            </a>
            <a
              href=""
              style="margin: 10px; cursor: pointer; border-radius: 999px">
              <img
                src="/linkedin.png"
                style="border-radius: 999px"
                width="40">
            </a>
          </div>
          <h5
            class="uk-margin-remove"
            style="color:#a09d9c; text-align: center;">Powered by
            <a
              href="https://prodequa.com/"
              target="_blank"
              style="text-decoration:none;color:white !important;">Prodequa &reg;</a>
          </h5>
        </div>
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
        {name:"logo"},
        {name:'¿POR QUÉ ELEGIRNOS?', url:'#Pilars'},
        {name:'CONTÁCTANOS', url:'#Contact'}
      ],
      src:''
    }
  },
  async mounted(){
    await this.$nextTick()
    await wait(1000)
    this.src = this.$store.getters.getInfoGeneral.logo
    LoadImage(this.src)
  },
  methods: {
    goTo (section, label) {

      UIkit.offcanvas('#offcanvas-nav-primary').hide().then(() => {
        //Validate screeen size
        UIkit.scroll({offset: 0}).scrollTo(section)
      })

      if (window.outerWidth > 960){
        UIkit.offcanvas('#offcanvas-nav-primary').hide().then(() => {
        //Validate screeen size
          UIkit.scroll({offset: 0}).scrollTo(section)
        })
      }
      else{
        UIkit.offcanvas('#offcanvas-nav-primary').hide().then(() => {
        //Validate screeen size
          UIkit.scroll({offset: 0}).scrollTo(section)
        })
      }

    },
    filterImage (url){
      return process.env.API_URL + url
    }
  }
}
function wait(n) {
   return new Promise(function(resolve, reject) {
    setTimeout(() => {
      resolve()
    }, n)
  })
}
function LoadImage(url) {
  var img = new Image()
  var x = document.getElementById("logoHome")

  img.src = process.env.API_URL + url + "?_=" + (+new Date())

  img.onload = function() {
      x.src = img.src
  };
}
</script>

<style>
  .navStyle {

    background-color: transparent !important;
  }
  .bkg-color{
    background: rgba(0,0,0,0.5) !important;
  }

  .navBarStyle > a > p::after {
    transition: width 0.4s;
    position: absolute;
    height: 2px;
    width: 0%;
    left: 0;
    top: 110%;
    content: '';
    background-color: #faeb05;
  }
  .navBarStyle:hover > a > p::after {
    width: 100%;
}
  .navItemStyle {
    margin-left: 1em;
    margin-right: 1em;
    white-space: normal !important;
  }

  .textElementsNav {
    font-family: 'Futura';
    font-weight: 700 !important;
    color: white !important;
    font-size: 16px;
    width: 78%;
  }
  .navOffCanvasElementStyle {
    padding: 1em;
    min-height: 0px !important;
  }
  .navOffCanvasTextStyle {
    color:white !important;
    font-size: 16px !important;
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
      width: 95%;
  }
  }
</style>
