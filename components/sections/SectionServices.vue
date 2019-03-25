<template>
  <div 
    style="background-image: url(/tramas.png);background-size:cover;background-position:50% 50%; width:100%; heigth:100%; background-color:#303e48;"
    class="uk-height-viewport uk-height-1-1">
    <div
      class="uk-padding" 
      style="text-align:center;">
      <h2 class="title-services"> {{ services.serviceSectionTitle }} </h2>
    </div>
    <div 
      v-if="services.service"
      class="uk-flex uk-width-1-2 ">
      <div
        v-for="(ele, key) in services.service"
        :key="key">
        <img 
          :src="ele.singleService.singleServiceImage"
          class="img-services"
          style="width:60%;" 
          alt="...">
        <div 
          style="">
          <a class="button-portrait">{{ ele.singleService.singleServiceName }}</a>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
export default {
    props:{
        services:{
            type: Object,
            default: function(){
                return {message:'events'}
            }
        }
    }
}
</script>

<style>
    .img-services{
        border-radius: 20px;
    }
    .title-services{
        font-weight: bold;
        color: black;
    }
    .button-portrait{
  background: url('/boton-1.png') no-repeat;
  background-size: cover;
  padding: 30px 45px;
  text-decoration: none;
  color: #303e48;
  font-weight: bold;
}
@media (max-width: 420px){
  .button-portrait{
    background: url('/boton-1.png') no-repeat;
    background-size: cover;
    padding: 25px 30px;
    text-decoration: none;
    color: #303e48;
    font-weight: bold;
}
}
</style>
