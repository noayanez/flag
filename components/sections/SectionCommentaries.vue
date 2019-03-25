<template>
  <div
    id="Commentaries"
    class="paddingForSlider uk-flex uk-flex-column uk-flex-center uk-flex-middle"
    style="background-color: lightblue; padding-left:10;">
    <div
      class="title-text uk-margin-remove uk-text-bold uk-padding-small uk-width-1-1 uk-text-center"
      style="color: black;">
      {{ commentaries.title }}
    </div>
    <div
      class="uk-flex uk-flex-center uk-flex-middle uk-width-1-1 uk-padding-small">
      <div class="uk-flex uk-flex-wrap uk-flex-center uk-flex-middle uk-width-4-5@s">
        <div
          v-for="(item, i) in commentaries.commentariesItems"
          :key="i"
          class="uk-position-relative uk-width-1-3@xl uk-width-1-2@m uk-padding-small uk-padding-remove-vertical">
          <div
            class="uk-text-center uk-flex uk-flex-center uk-flex-middle borderOpinion uk-width-1-1"
            style="color: black; padding: 50px; padding-bottom:75px;">
            <div
              class="uk-position-relative"
              style="height: 10%;">
              <div class="uk-overflow-auto">
                <p
                  class=""
                  style=" margin: 0px; height: 150px; padding-right: 10px">
                  {{ item.commentary }}
                </p>
              </div>
            </div>
          </div>
          <div
            class="uk-position-relative uk-flex uk-flex-row uk-flex-center uk-width-1-1"
            style="top: -50px;">
            <div
              class="uk-flex uk-flex-row uk-flex-left uk-width-1-1"
              style="padding-left: 3rem;">
              <div>
                <img
                  :src="item.imageUrl"
                  style=""
                  width="70px">
              </div>
              <div>
                <p
                  class="uk-text-bold"
                  style="color: black; margin: 0; padding-left: 0.5rem; padding-right: 0.5rem;">
                  {{ item.name }}
                </p>
                <p
                  style="color: black; margin: 0; padding-left: 0.5rem; padding-right: 0.5rem;">
                  {{ item.charge }}
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    commentaries: {
      type: Object,
      default: null
    }
  },
  data() {
    return {}
  }
}
</script>

<style lang="scss" scoped>
@media (max-width: 480px) {
  #opiniones{
    font-size: 14px !important;
    h1 {
      font-size: 14px !important;
    }
  }
}
.borderOpinion{
  border:2px solid;
  border-image-source: linear-gradient(#4f858d, #1d2d5e);
  border-image-slice: 1;
}
::-webkit-scrollbar {
  width: 10px;
  height: 10px;
  margin-left: 10px;
}
/* Track */
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px grey;
  border-radius: 10px;
}
/* Handle */
::-webkit-scrollbar-thumb {
  background: #ddd;
  border-radius: 10px;
}
/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #b2b2b2;
}
.title-text {
  font-size: 20px;
}
.subitle-text {
  font-size: 15px;
}
.description-text {
  font-size: 13px;
}
@media (min-width: 600px) {
  .title-text {
    font-size: 40px;
  }
  .subitle-text {
    font-size: 25px;
  }
  .description-text {
    font-size: 20px;
  }
}
.paddingForSlider {
  padding-top: 3rem;
  padding-bottom: 3rem;
}
@media (min-width: 550px) {
  .paddingForSlider {
    padding: 3rem;
  }
}
</style>
