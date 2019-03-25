<template>
  <div
    id="Products"
    class="uk-padding uk-flex uk-flex-column uk-flex-center uk-flex-middle"
    style="background-color:#e41c43; padding-left:10; min-height: 100vh;">
    <div
      class="uk-flex uk-flex-center uk-width-1-1 uk-padding">
      <div
        class="title-text uk-text-bold uk-text-center"
        style="color: #e41c43; background-color: white; border-radius: 20px;">
        {{ products.title }}
      </div>
    </div>
    <div
      class="uk-width-1-1"
      uk-slider>
      <div
        class="tam-fixed uk-position-relative uk-visible-toggle uk-dark padding-slider uk-width-1-1">
        <ul class="tam-fixed uk-slider-items uk-width-1-1 uk-child-width-1-2 uk-child-width-1-3@s">
          <li
            v-for="(item, key) in products.productsItems"
            :key="key"
            class="tam-fixed uk-padding-small"
            style="background-color:transparent;">
            <div
              :style="'background-image: url('+item.imageUrl+');'"
              style="background-size: cover; background-position: center; height:100%;"
              class=""
            />
          </li>
        </ul>
        <a
          class="uk-position-center-left uk-position-small uk-hidden-hover"
          href="#"
          uk-slider-item="previous">
          <svg
            width="25"
            height="40"
            viewBox="0 0 25 40"
            xmlns="http://www.w3.org/2000/svg">
            <polyline
              fill="none"
              stroke="#ffffff"
              stroke-width="2"
              points="20.527,1.5 2,20.024 20.525,38.547" />
          </svg>
        </a>
        <a
          class="uk-position-center-right uk-position-small uk-hidden-hover"
          href="#"
          uk-slider-item="next">
          <svg
            width="25"
            height="40"
            viewBox="0 0 25 40"
            xmlns="http://www.w3.org/2000/svg">
            <polyline
              fill="none"
              stroke="#ffffff"
              stroke-width="2"
              points="4.002,38.547 22.527,20.024 4,1.5 " />
          </svg>
        </a>
      </div>
      <ul class="uk-slideshow-nav uk-dotnav uk-flex-center dotnav-programs uk-padding-small" />
    </div>
    <div class="uk-flex uk-flex-column uk-flex-center uk-flex-middle uk-width-1-1">
      <div
        class="subtitle-text uk-margin-remove uk-padding-small uk-width-1-1 uk-text-center"
        style="color:white; font-weight:bolder !important">
        {{ products.subtitle }}
      </div>
      <div
        class="description-text uk-padding-small uk-padding-remove-vertical"
        style="color:white; margin-bottom:0px; text-align: justify;">
        {{ products.description }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props:{
    products:{
      type: Object,
      default: null
    }
  }
}
</script>

<style scoped>
.zoom {
  transition: all 0.5s ease;
}
.zoom:hover {
  transform: scale(1.1);
}
.title-text {
  font-size: 30px;
  padding: 0.5rem;
}
.subtitle-text {
  font-size: 20px;
}
.description-text {
  font-size: 15px;
}
@media (min-width: 600px) {
  .title-text {
    font-size: 40px;
  }
  .subtitle-text {
    font-size: 25px;
  }
  .description-text {
    font-size: 20px;
  }
}
.tam-fixed {
  min-height: 400px;
}
@media (max-width: 959px) {
  .tam-fixed {
    min-height: 300px;
  }
}
@media (max-width: 479px) {
  .tam-fixed {
    min-height: 200px;
  }
}
</style>
