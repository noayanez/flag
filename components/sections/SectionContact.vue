<template>
  <div 
    id="Contact"
    class="uk-flex uk-flex-wrap"
    style="background-image: url(/manchas.png);background-color: black;opacity:0.9;">
    <div
      class="uk-flex uk-flex uk-width-1-2@s uk-width-1-1 container-section-contact"
      style="">
      <div 
        class="background-contact"
        style="padding-top:30px;padding-bottom: 40px;">
        <h2
          class="uk-text-uppercase"
          style="text-align:center; color:white; font-weight: bold">¿Quieres conectar<br> con tus clientes?</h2>

        <h4 style="text-align:left;color:white; width: 80%;margin:auto">Completa el formulario y comencemos a crear nuevas experiencias</h4>
        <div class="uk-width-1-1">
          <div class="uk-width-1-1">
            <form 
              class="uk-grid uk-margin-remove container-form uk-width-1-1"
              @submit.prevent="send">
              <div class="uk-padding-remove container-form-left container-form-right uk-width-1-1">
                <div class="container-input">
                  <input 
                    v-model="form.name"
                    class="uk-input input-style" 
                    type="text"
                    pattern="[a-zA-ZñÑáéíóúÁÉÍÓÚ\s]+"
                    placeholder="Nombres">
                </div>
                <div class="container-input">
                  <input
                    v-model="form.email"
                    class="uk-input input-style" 
                    type="text"
                    pattern="[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,3}$"
                    placeholder="Correo:">
                </div>
                <div class="container-input">
                  <input 
                    v-model="form.phone"
                    class="uk-input input-style" 
                    type="text"
                    pattern="^(0|[0-9][0-9]*)$"
                    placeholder="Celular:">
                </div>
                <div class="container-input">
                  <textarea
                    v-model="form.message"
                    class="uk-textarea text-area-style"
                    placeholder="Mensaje:"/>
                </div> 
                <div style="padding-top: 10px;padding-bottom: 20px;">
                  <input
                    v-model="form.proteccion"  
                    type="checkbox"
                    name="proteccion" 
                    value="proteccion"
                    style="border:2px solid #faeb05"><span style="color:#faeb05">Protección de datos personales</span>
                </div>
              </div>
              <a
                style="text-decoration: none;color:#303e48; margin:auto">
                <div 
                  class="button-portrait uk-text-uppercase"
                  style="">
                  CONTACTAR </div></a> 
            </form>
          </div>
        </div>
      </div>
    </div>
    <div
      style="background-image: url(foto-footer.png);background-position: 50% 50%;background-size: cover;display: flex; justify-content: center; align-items:center;"
      class="uk-width-1-2@m uk-height-1-1 uk-padding  containerImgeContact">
      <div 
        class="uk-width-1-1"
        style="">
        <div
          class="container-footer-contact" 
          style="padding-bottom: 60px;">
          <h2 
            class="uk-text-uppercase"
            style="color: white;">CONTÁCTANOS</h2>
          <div class="padding-bottom">
            <a 
              href=""
              class="padding-right">
              <img 
                width="10%"
                src="/ubicación.png" 
                alt="...">
            </a>
            <span style="color:#faeb05">Alcanfores 495 of 608 Miraflores</span>
          </div>
          <div class="padding-bottom">
            <a 
              href=""
              class="padding-right">
              <img 
                width="10%"
                src="/correo.png" 
                alt="...">
            </a>
            <span style="color:#faeb05">marketing@flagsgroup.net</span>
          </div>
          <div class="padding-bottom">
            <a 
              href=""
              class="padding-right">
              <img 
                width="10%"
                src="/teléfono.png" 
                alt="...">
            </a>
            <span style="color:#faeb05">488 7910</span>
          </div>
        </div>
        <div
          class="container-footer-contact" 
          style="">
          <h2 style="color:white">SÍGUENOS</h2>
          <div class="padding-bottom">
            <a 
              href=""
              class="padding-right" >
              <img 
                width="10%"
                src="/facebook.png" 
                alt="...">
            </a>
            <span style="color:#faeb05"> THE FLAGS GROUP</span>
          </div>
          <div class="padding-bottom">
            <a 
              href=""
              class="padding-right" >
              <img 
                width="10%"
                src="/INSTAGRAM.png" 
                alt="...">
            </a>
            <span style="color:#faeb05"> THE FLAGS GROUP</span>
          </div>
          <div class="padding-bottom">
            <a 
              href=""
              class="padding-right">
              <img 
                width="10%"
                src="/linkedin.png" 
                alt="...">
            </a>
            <span style="color:#faeb05">THE FLAGS GROUP</span>
          </div>
        </div>
        <div
          class="uk-padding-large copy-right" 
          style="">
          <h5
            style="color:#a09d9c">Powered by <a 
              href="https://prodequa.com/" 
              target="_blank"
              style="text-decoration:none;color:white !important;"> Prodequa &reg;</a> </h5>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    contactForm: {
      type: Array,
      default: null
    },
    contact: {
      type: Object,
      default: null
    }
  },
  data() {
    return {
      title: '¡CONTÁCTANOS!',
      footer:{},
      form:{}
    }
  }
}
</script>

 <style lang="scss" scoped>
.copy-right{
    text-align: center;
    color:white;
    padding-top: 30px;
   position:relative;
   top:100px;
}

.container-footer-contact{
  padding-left:50px;
  width: 50%; 
  margin:auto;
}
.container-section-contact{
  padding-left:100px;
  padding-top: 65px;
  padding-bottom: 65px;  
  min-height: 80vh;
}
.background-contact{
    background-color: #414141;
    opacity: 0.9;
    filter:  alpha(opacity=40);
    border-radius: 10px;
    width: 60%;
}
.padding-right{
  padding-right: 10px;
}
.padding-bottom{
  padding-bottom: 10px;
}
.containerImgeContact{
    padding-top: 60px;
    min-width: 300px;
    background-size:cover; 
    background-position:50% 50%; 
    height:90vh;
    width: 50%;
}
.button-portrait{
  background: url('/boton-1.png') no-repeat;
  background-size: cover;
  padding: 41px 103px 26px 73px;
  text-decoration: none;
  color: #303e48;
  font-weight: bold;
  width:20%; 
  margin:auto
}

.title-style {
    font-weight: bold;
    color: #0b496e;
  }

  .subtitle-style {
    font-size: 13px;
  }

  .input-style {
    font-size: 18px;
    color: white !important;
    padding-left: 3%;
    padding-right: 3%;
    border-bottom: 3px solid white;
    border-top: none;
    border-right: none;
    border-left: none;
    background-color: transparent;
  }

  .text-area-style {
    padding-left: 3%;
    padding-right: 3%;
    height: 50px !important;
    border-bottom: 3px solid white;
    border-top: none;
    border-right: none;
    border-left: none;
    background-color: transparent;
  }

  .btn-more-information {
    background-color: #1f8884;
    font-weight: bolder;
    color: white;
    border-radius: 10px;
    border: none;
  }

  .container-input {
    padding-top: 15px !important;
  }
  @media(max-width: 780px){
    .container-footer-contact{
      width: 90%;
    
    }
  }

  @media (max-width: 640px) {
    .title-style {
      font-size: 18px;
    }
    .copy-right{
      top:20px;
    }

    .container-subtitle{
      padding-left: 2%;
      padding-right: 2%;
    }

    .input-style {
      font-size: 13px;
      height: 40px !important;
    }

    .text-area-style {
      height: 50px !important;
      font-size: 18px;
    }
    
    .btn-more-information{
      font-size: 12px;
      padding-top: 3%;
      padding-bottom: 3%;
      padding-left: 7%;
      padding-right: 7%;
    }

    .container-btn-more-information {
      padding-top:8% !important;
    }

    .container-form-left {
      padding-right: 3% !important;
    }

    .container-form-right {
      padding-left: 3% !important;
    } 
    .background-contact{
      width: 100%;
    }    
    .container-section-contact{
      padding-left: 30px;
      padding-right: 30px;
    }  
    .containerImgeContact{
      width: 100%;
    }
  }

  @media (min-width: 640px) and (max-width: 959px){
    .title-style {
      font-size: 18px;
    }

    .container-subtitle{
      padding-left: 2%;
      padding-right: 2%;
    }

    .input-style {
      font-size: 13px;
      height: 50px !important;
    }

    .text-area-style {
      height: 60px !important;
      font-size: 18px;
    }
    
    .btn-more-information{
      font-size: 13px;
      padding-top: 2%;
      padding-bottom: 2%;
      padding-left: 4%;
      padding-right: 4%;
    }

    .container-btn-more-information {
      padding-top:8% !important;
    }

    .container-form-left {
      padding-right: 3% !important;
    }

    .container-form-right {
      padding-left: 3% !important;
    }  
    .container-section-contact{
      padding-left:30px; 
      padding-right: 20px;
    }  
    .background-contact{
      width: 100%;
    }
  }
  @media (min-width: 960px) and (max-width: 1025px){
    .background-contact{
      width: 100%;
    }
    .container-section-contact{
      padding-left:30px; 
      padding-right: 20px;
    }
  }
  @media (min-width: 1025px) {

    .title-style {
      font-size: 23px;
    }

    .input-style {
      font-size: 18px;
      height: 70px !important;
    }

    .container-subtitle {
      padding-left: 35%;
      padding-right: 35%;
    }

    .container-form {
      padding-left: 10%;
      padding-right: 10%;
    }

    .container-form-left {
      padding-right: 5% !important;
    }

    .container-form-right {
      padding-left: 0% !important;
    }

    .btn-more-information{
      font-size: 15px;
      padding-top: 1.3%;
      padding-bottom: 1.3%;
      padding-left: 4%;
      padding-right: 4%;
    }

    .container-btn-more-information {
      padding-top:2% !important;
    }

    .text-area-style {
      height: 60px !important;
      font-size: 18px;
    }
    .container-section-contact{
      padding-left: 100px;
    }
    
  }
 </style>
