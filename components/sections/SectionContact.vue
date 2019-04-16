<template>
  <div
    id="Contact"
    class="uk-flex uk-flex-wrap uk-flex-center uk-flex-middle"
    style="height: 100vh;">
    <div
      class="uk-width-1-2@m uk-width-1-1"
      style=" background: #000000e5; height: 100vh;">
      <div
        class="uk-width-1-1 uk-height-1-1 uk-flex uk-flex-around uk-flex-middle"
        style="background-image: url('/manchas.png'); background-position: center; background-size: cover;">
        <div
          class="uk-width-1-1 uk-height-1-1 uk-flex uk-flex-center uk-flex-bottom"
          style="background: #000000cc; padding-bottom: 15px; padding-left: 10px; padding-right: 10px; padding-top: 70px;">
          <div
            class="uk-width-4-5@m uk-width-1-1 uk-flex uk-flex-column uk-flex-center uk-flex-middle padder-1 heighter-contact"
            style="border-radius: 8px; background: #ffffff44;">
            <div
              class="uk-width-1-1 titleless uk-flex uk-flex-column uk-flex-around uk-flex-middle remove-margin"
              style="height: 25%;">
              <div class="uk-width-1-1 uk-flex uk-flex-left@s uk-flex-center uk-flex-middle">
                <div
                  class="uk-width-1-1 uk-text-uppercase text-title uk-text-left@m uk-text-center"
                  style="color: white; font-weight: 800 !important; font-family: futura !important;">
                  ¿Quieres conectar <br> con tus clientes?
                </div>
              </div>
              <div
                class="uk-width-1-1 text-subtitle"
                style="text-align:left; color:white; font-weight: 700 !important; font-family: futura !important;">
                Completa el formulario y comencemos a crear nuevas experiencias:
              </div>
            </div>
            <form
              name="form1"
              class="uk-margin-remove uk-width-1-1 uk-flex uk-flex-column uk-flex-around uk-flex-middle"
              style=""
              @submit.prevent="send">
              <div
                class="uk-width-1-1 container-input remove-margin remove-padding"
                style="padding-top: 10px; padding-bottom: 10px;">
                <input
                  v-validate.imediate="{ required: true }"
                  v-model="form.name"
                  name="Nombres"
                  class="uk-input input-styled"
                  style="background: transparent; border-color: white; border-width: 0px 0px 1px 0px; color: white; height: 30px; padding: 0 !important;"
                  type="text"
                  pattern="[A-Za-z ]*"
                  placeholder="Nombres">
              </div>
              <div
                class="uk-width-1-1 container-input remove-margin remove-padding"
                style="padding-top: 10px; padding-bottom: 10px;">
                <input
                  v-validate.imediate="{numeric: true,required: true }"
                  v-model="form.phone"
                  name="phone"
                  class="uk-input input-styled"
                  style="background: transparent; border-color: white; border-width: 0px 0px 1px 0px;color: white; height: 30px; padding: 0 !important; "
                  type="text"
                  pattern="^[1-9][0-9]{8}$"
                  placeholder="Celular:">
              </div>
              <div
                class="uk-width-1-1 container-input remove-margin remove-padding"
                style="padding-top: 10px; padding-bottom: 10px;">
                <input
                  v-validate.imediate="{ required: true, email: true }"
                  v-model="form.email"
                  name="email"
                  class="uk-input input-styled"
                  style="background: transparent; border-color: white; border-width: 0px 0px 1px 0px;color: white; height: 30px; padding: 0 !important;"
                  type="email"
                  pattern="[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,3}$"
                  placeholder="Correo:">
              </div>
              <div
                class="uk-width-1-1 container-input remove-margin remove-padding"
                style="padding-top: 10px; padding-bottom: 10px;">
                <textarea
                  v-model="form.message"
                  name="message"
                  style="background: transparent; border-color: white; border-width: 0px 0px 1px 0px; color: white; padding: 0;"
                  class="uk-textarea input-styled"
                  rows="2"
                  placeholder="Mensaje:"/>
              </div>
              <div
                class="uk-position-relative uk-width-1-1 uk-flex uk-flex-left@m uk-flex-center uk-flex-middle"
                style="margin-top: 5px; margin-bottom: 5px; height: 25px !important;">
                <div
                  class="uk-position-relative uk-width-1-1 uk-flex uk-flex-left@m uk-flex-center uk-flex-middle"
                  style="margin-top: 10px; margin-bottom: 10px; height: 25px !important;">
                  <label
                    class="uk-position-relative container uk-height-1-1">
                    <input type="checkbox">
                    <span class="checkmark"/>
                  </label>
                  <div
                    class="protect"
                    style="font-family: futura; color: yellow; font-weight: 600 !important;">
                    Proteccion de datos personales
                  </div>
                </div>
              </div>
              <div
                class="uk-width-auto@s uk-width-1-1 uk-flex uk-flex-center uk-flex-middle remove-margin"
                style="margin-top: 15px; margin-bottom: 15px;">
                <div style="background-image: url('/boton-1.png'); background-repeat: no-repeat; background-size: cover; background-position: center; height: 72px; width: 160px;">
                  <button
                    type="submit"
                    class="uk-text-center uk-flex uk-flex-center uk-flex-middle uk-width-1-1 uk-height-1-1"
                    style="margin-top: 5px; background: transparent; font-family: futura; font-weight: 800; color: #000000cc; font-size: 0.95rem; border:none; cursor: pointer; outline: none;">
                    CONTACTAR
                  </button>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
    <div
      class="uk-position-relative uk-width-1-2@m uk-width-1-1 uk-flex uk-flex-column uk-flex-center uk-flex-middle"
      style="background-image: url('foto-footer.png'); background-repeat: no-repeat; background-size: cover; background-position: center; height: 100vh; padding-top: 3.5%;">
      <div
        uk-flex
        class="uk-width-1-1 uk-flex uk-flex-center uk-flex-middle"
        style="">
        <div class="uk-width-1-1 uk-flex uk-flex-column uk-flex-center uk-flex-middle">
          <div
            class="uk-width-2-5@m uk-width-4-5 "
            style="margin-left: 50px; margin-bottom: 20px;">
            <h3
              class="uk-text-uppercase uk-width-1-1 uk-text-left"
              style="color: white;">CONTÁCTANOS</h3>
            <div
              class="uk-flex uk-flex-left uk-flex-middle uk-width-1-1"
              style="margin-bottom:15px;">
              <a
                href=""
                style="width: 30px; margin-right: 10px;"
                class="">
                <img
                  src="/ubicación.png"
                  width="30px"
                  alt="...">
              </a>
              <span class="uk-width-4-5 letra-footer">{{ footer.officeAddress }}</span>
            </div>
            <div
              class="uk-flex uk-flex-left uk-flex-middle uk-width-1-1"
              style="margin-bottom:15px;">
              <a
                href=""
                style="width: 30px; margin-right: 10px;"
                class="">
                <img
                  src="/correo.png"
                  width="30px"
                  alt="...">
              </a>
              <span class="uk-width-4-5 letra-footer">{{ footer.email }}</span>
            </div>
            <div
              class="uk-flex uk-flex-left uk-flex-middle uk-width-1-1"
              style="margin-bottom:15px;">
              <a
                href=""
                style="width: 30px; margin-right: 10px;"
                class="">
                <img
                  src="/teléfono.png"
                  width="30px"
                  alt="...">
              </a>
              <span class="uk-width-4-5 letra-footer">{{ footer.phone }}</span>
            </div>
          </div>
          <div
            class="uk-width-2-5@m uk-width-4-5 "
            style="margin-left: 50px; margin-bottom: 0px;">
            <h3
              class="uk-text-uppercase uk-width-1-1 uk-text-left"
              style="color: white;">SÍGUENOS</h3>
            <div
              class="uk-flex uk-flex-left uk-flex-middle uk-width-1-1"
              style="margin-bottom:15px;">
              <a
                href=""
                style="width: 30px; margin-right: 10px;"
                class="">
                <img
                  src="/facebook.png"
                  width="30px"
                  alt="...">
              </a>
              <span class="uk-width-4-5 letra-footer">{{ footer.facebook }}</span>
            </div>
            <div
              class="uk-flex uk-flex-left uk-flex-middle uk-width-1-1"
              style="margin-bottom:15px;">
              <a
                href=""
                style="width: 30px; margin-right: 10px;"
                class="">
                <img
                  src="/INSTAGRAM.png"
                  width="30px"
                  alt="...">
              </a>
              <span class="uk-width-4-5 letra-footer">{{ footer.instagram }}</span>
            </div>
            <div
              class="uk-flex uk-flex-left uk-flex-middle uk-width-1-1"
              style="margin-bottom:15px;">
              <a
                href=""
                style="width: 30px; margin-right: 10px;"
                class="">
                <img
                  src="/linkedin.png"
                  width="30px"
                  alt="...">
              </a>
              <span class="uk-width-4-5 letra-footer">{{ footer.linkedin }}</span>
            </div>
          </div>
        </div>
      </div>

      <div
        class="uk-padding-large copy-right uk-padding-remove"
        style="position: absolute; bottom: 0; top: auto !important;">
        <h5
          style="color:#a09d9c">Powered by <a
            href="https://prodequa.com/"
            target="_blank"
            style="text-decoration:none;color:white !important;"> Prodequa &reg;</a> </h5>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    footer: {
      type: Object,
      default: null
    }
  },
  data() {
    return {
      title: '¡CONTÁCTANOS!',
      form:{
        name: '',
        email: '',
        message: '',
        phone: '',
        proteccion: ''
      },
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
      if (this.form.email==='' || this.form.message==='' || this.form.name==='' || this.form.phone==='') {
        return
      }
      const formData = {
        email : this.form.email,
        message: this.form.message,
        name: this.form.name,
        phone: this.form.phone,
        need: this.form.proteccion || false
      }
      console.log(formData);
      let res =  await this.$axios.post('/site/contact/form', formData)
      console.log(res);
    }
  }
}
</script>

<style lang="scss" scoped>
.protect {
  font-size: 14px;
  margin-left: 12px !important;
}
@media (min-width: 1200px) and (min-height: 600px){
  .protect {
    font-size: 18px !important;
    margin-left: 20px !important;
  }
}
input[type="number"]::-webkit-outer-spin-button, input[type="number"]::-webkit-inner-spin-button {
  appearance: none;
}
input[type="number"] {
  appearance: textfield !important;
}
.flexeador {
  justify-content: center;
}
@media (max-height: 600px) {
  .flexeador {
    justify-content: flex-end;
  }
}
.heighter-contact {
  height: 98%;
}
@media (max-height: 640px) {
  .text-title {
    font-size: 1.2rem !important;
  }
  .text-subtitle {
    font-size: 1rem !important;
  }
  .heighter-contact {
    height: 97%;
  }
  .remove-margin {
    margin: 0 !important;
  }
  .remove-padding {
    padding-bottom: 5px !important;
    padding-top: 0 !important;
  }
}
.container-input {
  margin: 5px 0;
}
.text-title {
  font-size: 2.2rem;
}
.text-subtitle {
  font-size: 1.5rem;
}
.input-styled {
  font-size: 1rem;
  border-radius: 0px;
}
@media (max-width:1800px) {
  .text-title {
    font-size: 1.8rem;
  }
  .text-subtitle {
    font-size: 1.2rem;
  }
}
@media (max-width:1400px) {
  .text-title {
    font-size: 1.5rem;
  }
  .text-subtitle {
    font-size: 1rem;
  }
}
@media (max-width:960px) {
  .text-title {
    font-size: 1.4rem;
  }
  .text-subtitle {
    font-size: 1rem;
    text-align: center !important;
  }
  .input-styled {
    font-size: 0.8rem;
  }
}
.letra-footer {
  color:#faeb05;
  font-size:1.2rem;
}
@media (max-width:1550px) {
  .letra-footer {
    color:#faeb05;
    font-size:1rem;
  }
}
.titleless {
  margin: 10px 0;
}
@media (min-width: 800px) {
  .titleless {
    margin: 10px 0;
  }
}
.padder-1 {
  padding: 0rem 3rem;
}
@media (max-width: 1200px) {
  .padder-1 {
    padding: 10px 28px;
  }
}
@media (max-width: 800px) {
  .padder-1 {
    padding: 10px 28px;
  }
}
::placeholder{
  color: white;
}
.container-devices {
  height: 737px;
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
  width: 82%;
  margin: auto;
  padding: 15px 0px 15px 0px;
  font-size: 2rem;
}
.padding-bottom-button{
  padding-bottom: 28px;
}
.background-contact{
    background-color: #414141;
    padding: 20px;
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
.title-style {
  font-weight: bold;
  color: #0b496e;
    font-size: 23px;
}
.subtitle-style {
  font-size: 13px;
}
.input-style {
  font-size: 1.5rem;
  color: white !important;
  padding-left: 3% !important;
  padding-right: 3% !important;
  border-bottom: 1px solid white;
  border-top: none;
  border-right: none;
  border-left: none;
  background-color: transparent;
  font-size: 18px;
  height: 50px !important;
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
.container-subtitle {
  padding-left: 35%;
  padding-right: 35%;
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
   -left {
    padding-right: 3% !important;
  }
   -right {
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
    font-size: 1.5rem;
  }
  .container-subtitle{
    padding-left: 2%;
    padding-right: 2%;
  }
  .input-style {
    font-size: 13px;
    height: 30px !important;
  }
  .text-area-style {
    height: 50px !important;
    font-size: 13px;
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
  .background-contact{
    width: 100%;
    padding-top: 15px;
    padding-bottom: 0px;
    padding-left: 0px;
    padding-right: 0px;
  }
  .containerImgeContact{
    width: 100%;
  }
  .container-1{
    width: 100%;
  }
  .padding-bottom-button{
    padding-bottom: 10px;
  }
}
@media(max-width: 780px){
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
    height: 30px !important;
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
  .background-contact{
    width: 100%;
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
@media (min-width: 1026px) and (max-width: 1369px){
  .title-contact-style{
    font-size: 1.7rem;
    padding: 15px 0px;
  }
  .container-input{
    padding-bottom: 4px;
    padding-top: 4px;
  }
  .text-area-style{
    height: 48px !important;
  }
  .background-contact{
    padding-bottom: 0px;
  }
}
::placeholder {
  color: rgb(214, 214, 214);
}

/* The container */
.container {
  display: block;
  position: relative;
  // padding-left: 15px;
  cursor: pointer;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/* Hide the browser's default checkbox */
.container input {
  opacity: 0;
  cursor: pointer;
  height: 100%;
}

/* Create a custom checkbox */
.checkmark {
  position: absolute;
  top: 0;
  height: 20px;
  width: 20px;
  background-color: transparent;
  border-color: yellow;
  border-radius: 8px;
  border: solid 2px yellow;
}

/* On mouse-over, add a grey background color */
.container:hover input ~ .checkmark {
  background-color: rgba(255, 255, 0, 0.25);
}

/* When the checkbox is checked, add a blue background */
.container input:checked ~ .checkmark {
  background-color: transparent;
}

/* Create the checkmark/indicator (hidden when not checked) */
.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

/* Show the checkmark when checked */
.container input:checked ~ .checkmark:after {
  display: block;
}

/* Style the checkmark/indicator */
.container .checkmark:after {
  left: 6px;
  top: 2px;
  width: 5px;
  height: 10px;
  border: solid yellow;
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}
 </style>
