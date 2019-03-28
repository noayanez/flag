<template>
  <div
    id="Footer"
    class="uk-flex uk-width-1-2"
    style="background: transparent; min-height: 80vh;">
    <div
      v-if="loaded"
      class="uk-flex uk-flex-column uk-flex-center uk-flex-middle uk-padding uk-width-1-1">
      <div class="uk-flex uk-flex-wrap uk-flex-center uk-flex-around uk-width-1-1">
        <div
          v-for="(item, i) in footerContent.items1"
          :key="i"
          class="uk-flex uk-flex-column uk-flex-center alignFooter uk-width-1-3@m uk-width-1-1 uk-padding-small uk-padding-remove-bottom"
          style="color: white;">
          <div
            class="uk-flex uk-flex-center uk-flex-middle"
            style="padding-bottom: 0.5rem;">
            <img :src="item.imageUrl">
            <div
              class="uk-padding-small uk-padding-remove-vertical"
              style="font-size: 25px;">
              {{ item.title }}
            </div>
          </div>
          <div
            class="uk-flex uk-flex-center uk-flex-middle"
            style="padding-bottom: 0.5rem;">
            <a
              :href="item.external.url"
              :target="item.external.type==='mail'? '':'_blank'"
              style="font-size: 20px; text-decoration: none; color: white;">
              <div class="uk-text-center">
                {{ item.external.text }}
              </div>
            </a>
          </div>
        </div>
      </div>
      <div
        class="uk-flex uk-flex-wrap uk-flex-center uk-flex-around uk-width-1-1"
        style="padding-bottom: 2rem;">
        <div
          v-for="(item, i) in footerContent.items2"
          :key="i"
          class="uk-flex uk-flex-column uk-flex-center alignFooter uk-width-1-3@m uk-width-1-1 uk-padding-small uk-padding-remove-bottom"
          style="color: white;">
          <div
            v-if="item.type==='1'">
            {{ item.information }}
          </div>
          <div
            v-else
            class="uk-flex uk-flex-center uk-flex-middle">
            <div
              v-for="(info,j) in item.information"
              :key="j"
              style="padding-left: 0.25rem; padding-right: 0.25rem;">
              <a
                :href="info.url"
                target="_blank">
                <img :src="info.imageUrl">
              </a>
            </div>
          </div>
        </div>
      </div>
      <div class="barLine" />
      <div
        class="uk-flex uk-flex-center uk-flex-middle uk-width-1-1"
        style="padding-top: 1.5rem;">
        <div
          style="color: white; padding-right: 0.5rem;">
          Powered by
        </div>
        <div>
          <a
            :href="footerContent.developed.url"
            target="_blank"
            class="uk-text-bold"
            style="text-decoration: none; color: white;">
            Prodequa
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    footer: {
      type: Object,
      default: null,
    }
  },
  data() {
    return {
      loaded: false,
      footerContent: ''
    }
  },
  mounted() {
    this.footerContent = {
      items1: [
        {
          imageUrl: 'http://tctechnology.com.pe/ubicacion.png',
          title: 'VISÍTANOS',
          external: {
            type: 'map',
            text: (this.footer.address? this.footer.address:('')),
            url: (this.footer.map? this.footer.map:(''))
          }
        },
        {
          imageUrl: 'http://tctechnology.com.pe/wssp.png',
          title: 'LLÁMANOS',
          external: {
            type: 'wssp',
            text: (this.footer.phone? this.footer.phone:('')),
            url: (this.footer.phone? ('https://web.whatsapp.com/send?phone=+' + this.footer.phone):(''))
          }
        },
        {
          imageUrl: 'http://tctechnology.com.pe/correo_icono.png',
          title: 'ESCRÍBENOS',
          external: {
            type: 'mail',
            text: (this.footer.email? this.footer.email:('')),
            url: (this.footer.email? ('mailto:' + this.footer.email):(''))
          }
        }
      ],
      items2: [
        {
          type: '1',
          information: 'Términos y condiciones'
        },
        {
          type: '2',
          information: [
            {
              imageUrl: 'http://tctechnology.com.pe/facebook_icono.png',
              url: (this.footer.facebook? this.footer.facebook:(''))
            },
            {
              imageUrl: 'http://tctechnology.com.pe/linkedin_icono.png',
              url: (this.footer.linkedin? this.footer.linkedin:(''))
            },
            {
              imageUrl: 'http://tctechnology.com.pe/twitter_icono.png',
              url: (this.footer.twitter? this.footer.twitter:(''))
            }
          ]
        },
        {
          type: '1',
          information: 'Somos proveedores del Estado'
        }
      ],
      developed: {
        poweredBy: 'Powered by',
        developer: 'Prodequa',
        url: 'https://prodequa.com/'
      }
    }
    this.loaded = true
  },
  methods: {
    log(x) {
      console.log(x)
    }
  }
}
</script>

<style>
.alignFooter {
  align-items: center
}
@media (max-width: 959px) {
  .alignFooter {
    align-items: start
  }
}
.barLine {
  width: 100%;
  height: 2px;
  background: white;
}
</style>
