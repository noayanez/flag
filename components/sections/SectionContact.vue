<template>
  <div 
    id="Contact"
    class="uk-flex uk-flex-wrap uk-height-1-1"
    style="background-image: url(/manchas.png);background-color: black;opacity:0.9; filter:brightness(0.9);">
    <div
      :class="device ? 'container-devices' : 'uk-height-viewport'" 
      class="container-1">
      <div
        class="uk-flex uk-flex-center uk-flex-middle container-form-left container-form-right"
        style="padding-top:30px">
        <div 
          class="background-contact"
          style="">
          <h2
            class="uk-text-uppercase title-contact-style"
            style="text-align:left; color:white; font-weight: bold">¿Quieres conectar<br> con tus clientes?</h2>

          <h4 
            class="description-contact" 
            style="text-align:left;color:white;">Completa el formulario y comencemos a crear nuevas experiencias</h4>
          <div class="uk-width-1-1">
            <div class="uk-width-1-1">
              <form 
                name="form1"
                class="uk-grid uk-margin-remove container-form uk-width-1-1"
                @submit.prevent="send">
                <div class="uk-padding-remove container-form-left container-form-right uk-width-1-1">
                  <div class="container-input">
                    <input 
                      v-validate.imediate="{ required: true }"
                      v-model="form.name"
                      name="Nombres"
                      class="uk-input input-style" 
                      type="text"
                      placeholder="Nombres">
                  </div>
                  <span style="color:white;">{{ errors.first('name') }}</span>
                  <div class="container-input">
                    <input 
                      v-validate.imediate="{numeric: true,required: true }"
                      v-model="form.phone"
                      name="phone"
                      class="uk-input input-style" 
                      type="text"
                      pattern="^(0|[0-9][0-9]*)$"
                      placeholder="Celular:">
                  </div>
                  <span style="color:white;">{{ errors.first('phone') }}</span>
                  <div class="container-input">
                    <input
                      v-validate.imediate="{ required: true, email: true }"
                      v-model="form.email"
                      name="email"
                      class="uk-input input-style" 
                      type="email"
                      pattern="[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,3}$"
                      placeholder="Correo:">
                  </div>
                  <span style="color:white;">{{ errors.first('email') }}</span>
                  <div class="container-input">
                    <textarea
                      v-model="form.message"
                      name="message"
                      class="uk-textarea text-area-style"
                      placeholder="Mensaje:"/>
                    <textarea
                      v-model="form.message2"
                      name="message2"
                      class="uk-textarea text-area-style"/>
                  </div> 
                  <div 
                    class="width-container"
                    style="padding-top: 10px;padding-bottom: 48px;">
                    <input
                      v-model="form.proteccion"  
                      type="checkbox"
                      name="proteccion" 
                      value="proteccion"
                      style="border:2px solid #faeb05"><span style="color:#faeb05">Protección de datos personales</span>
                  </div>
                </div>
                <a
                  class="uk-padding-remove-left padding-bottom-button"
                  style="text-decoration: none;color:#303e48; margin:auto">
                  <input 
                    type="submit"
                    class="button-portrait uk-text-uppercase"
                    style="border:none"
                    value="CONTACTAR">
                </a> 
              </form>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div
      :class="device ? 'container-devices' : 'uk-height-viewport'"
      style="background-image: url(foto-footer.png)"
      class="uk-height-1-1 uk-padding  containerImgeContact">
      <div
        uk-flex
        uk-scrollspy="cls: uk-animation-scale-down; target: > div > div > div; delay: 250; repeat: true" 
        class="uk-width-1-1 uk-flex uk-flex-center uk-flex-middle"
        style="">
        <div class="">
          <div
            v-for="(el, key) in footer"
            :key="key"
            class="container-footer-contact" 
            style="padding-bottom: 60px;">
            <h3
              v-if="key==0"
              class="uk-text-uppercase"
              style="color: white;">CONTÁCTANOS</h3>
            <h3 
              v-else
              class="uk-text-uppercase"
              style="color:white">SÍGUENOS</h3>
            <div 
              v-for="(e, i) in el.items"
              :key="i"
              class="padding-bottom">
              <a 
                :href="e.imgUrl"
                class="padding-right">
                <img 
                  :src="e.src"
                  width="10%" 
                  alt="...">
              </a>
              <span style="color:#faeb05; font-size:1.2rem;">{{ e.title }}</span>
            </div>
          </div>
          <div
            uk-flex
            uk-scrollspy="cls: uk-animation-scale-down; target: > h5 ; delay: 450; repeat: true" 
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
  </div>
</template>

<script>
export default {
  props: {
    contact: {
      type: Object,
      default: null
    }
  },
  data() {
    return {
      title: '¡CONTÁCTANOS!',
      footer:[
        {
          items:[
            {
              imgUrl:"",
              src:"/ubicación.png",
              title:"Calle Alcanfores 495 of 608 Miraflores"
            },
            {
              imgUrl:"",
              src:"/correo.png",
              title:"marketing@flagsgroup.net"
            },
            {
              imgUrl:"",
              src:"/teléfono.png",
              title:"488 7910"
            }
          ]
        },
        {
          items:[
            {
              imgUrl:"",
              src:"/facebook.png",
              title:"THE FLAGS GROUP"
            },
            {
              imgUrl:"",
              src:"/INSTAGRAM.png",
              title:"THE FLAGS GROUP"
            },
            {
              imgUrl:"",
              src:"/linkedin.png",
              title:"THE FLAGS GROUP"
            }
          ]
        }
      ],
      form:{},
      device:''
    }},
  mounted(){
     var userAgent = navigator.userAgent || navigator.vendor || window.opera
    if (/iPad|iPhone|iPod/.test(userAgent) && !window.MSStream) {
      this.device = true
    }
  },
  methods:{
  async send(){
      const formData = {
        email : this.form.email,
        message: this.form.message + " " + this.form.message2 || this.form.message2,
        name: this.form.name,
        phone: this.form.phone,
        need: this.form.proteccion || false
      }
      console.log(formData);
      if(this.form!={}){
        let res =  await this.$axios.post('/site/contact/form', formData)
        console.log(res);
      }
    }
  }
}
</script>

 <style lang="scss" scoped>

  ::placeholder{
    color: white;
  }
 .container-devices {
    height: 737px;
}
.description-contact{
   width: 85%;
   margin:auto;
   padding-bottom:20px;
}
textarea{
  resize: none;
}
.copy-right{
  text-align: center;
  color:white;
  padding-top: 30px;
  position: asolute;
  top:100px;
}
.title-contact-style{
  width: 85%;
  margin: auto;
  padding-bottom: 35px;
  font-size: 2.3rem;
}
.padding-bottom-button{
  padding-bottom: 28px;
}

.container-footer-contact{
  padding-left:50px;
  width: 50%; 
  margin:auto;
}
.background-contact{
    padding-top:30px;
    padding-bottom: 40px;
    background-color: #414141;
    opacity: 0.9;
    filter:  alpha(opacity=40);
    border-radius: 10px;
    width: 70%;
}
.padding-right{
  padding-right: 10px;
}
.padding-bottom{
  padding-bottom: 10px;
}
.containerImgeContact{
    padding-top: 118px;
    min-width: 300px;
    background-size:cover; 
    background-position:50% 50%; 
    width: 55%;
    display: flex; 
    justify-content: center; 
    align-items:center;
}
.container-1{
  width: 45%;
}
.button-portrait{
  background: url('/boton-1.png') no-repeat;
  background-size: cover;
  padding: 42px 124px 40px 67px;
  text-decoration: none;
  color: #303e48;
  font-weight: bold;
  width: 80%; 
  margin:auto;
  font-size: 20px;
}

.title-style {
    font-weight: bold;
    color: #0b496e;
     font-size: 23px;
  }

  .subtitle-style {
    font-size: 13px;
  }

  .input-style {
    font-size: 1.25rem;
    color: white !important;
    padding-left: 3% !important;
    padding-right: 3% !important;
    border-bottom: 1.5px solid white;
    border-top: none;
    border-right: none;
    border-left: none;
    background-color: transparent;
    font-size: 18px;
    height: 70px !important;
  }

  .text-area-style {
    padding-left: 3%;
    padding-right: 3%;
    height: 84px !important;
    font-size: 18px;
    height: 65px !important;
    border-bottom: 1.5px solid white;
    border-top: none;
    border-right: none;
    border-left: none;
    background-color: transparent;
    color:white;
  }

  .btn-more-information {
    background-color: #1f8884;
    font-weight: bolder;
    color: white;
    border-radius: 10px;
    border: none;
    font-size: 15px;
    padding-top: 1.3%;
    padding-bottom: 1.3%;
    padding-left: 4%;
    padding-right: 4%;
  }

  .container-input {
    padding-top: 15px !important;
  }
  .container-subtitle {
    padding-left: 35%;
    padding-right: 35%;
    }
  .container-form {
      padding-left: 10%;
      padding-right: 10%;
      padding-bottom: 5px;
    }

    .container-form-right {
      padding-left: 0% !important;
    }
     .container-btn-more-information {
      padding-top:2% !important;
    }

  @media(max-width:320px){
    .containerImgeContact{
      padding-top: 10px;
   }
    .copy-right{
      top:220px;
   }
  .container-1{
    width: 100%;
  }
  .container-form-left {
      padding-right: 3% !important;
    }

    .container-form-right {
      padding-left: 3% !important;
    }
     .title-contact-style{
      font-size: 1.5rem;
    } 
  }
  @media (max-width: 640px) {
    .title-style {
      font-size: 18px;
    }
    .copy-right{
      top:20px;
    }
    .title-contact-style{
      width: 100%;
      padding-left: 13px;
      padding-bottom: 16px;
      padding-top: 15px;
      font-size: 1.5rem;
    }
    .description-contact{
      width: 90%;
      padding-left: 13px;
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
      padding-right: 8% !important;
    }

    .container-form-right {
      padding-left: 8% !important;
    } 
    .background-contact{
      width: 100%;
      padding: 0px 21px;
    }     
    .containerImgeContact{
      width: 100%;
    }
    .container-1{
      width: 100%;
    }
    .button-portrait{
      padding: 35px 106px 34px 53px;
    }
    .container-form{
      padding-bottom: 20px;
      padding-left: 2%;
      padding-right: 2%;
    }
  }
   @media(max-width: 780px){
    .container-footer-contact{
      width: 90%;
    }
    .title-contact-style{
      font-size: 1.5rem;
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
    .background-contact{
      width: 100%;
      padding-bottom: 59px;
    }
  }
  @media (min-width: 960px) and (max-width: 1025px){
    .background-contact{
      width: 93%;
    }
    .container-input{
      width: 85%;
      margin:auto;
    }
    .width-container{
      width: 85%;
      margin: auto;
    }
    .containerImgeContact {
        padding-top: 200px;
        align-items: start;
}
  }
  @media (min-width: 1026px) and (max-width: 1367px){
    .title-contact-style{
      font-size: 2rem;
      padding-bottom: 15px !important;
    }
    .container-input{
      padding-bottom: 0px;
      padding-top: 5px;
    }
    .button-portrait{
      padding: 37px 120px 34px 62px;
      font-size: 17px;
    }
    .input-style {
      height: 50px !important;
    }
    .text-area-style{
      height: 68px !important;
    }
    .background-contact{
      padding-bottom: 0px;
    }
    .description-contact{
      width: 86%;
      padding-bottom: 12px;
    }
}
 </style>
