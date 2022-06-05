<template>
  <div>
    <SplashScreen />
    <VueSlickCarousel v-bind="carousel" ref="carousel">
      <div v-for="(item, index) in onboardings" :key="index">
        <div class="center">
          <h1 class="text-center brand mt-15">PayUKT</h1>
          <v-img :src="item.imageUrl"></v-img>
          <h2 class="text-center subtitle">{{ item.subtitle }}</h2>
          <p class="text-center text">
            {{ item.text }}
          </p>
        </div>
      </div>
      <template #nextArrow="arrowOption">
        <div>
          {{ arrowOption.currentSlide }}/{{ arrowOption.slideCount }}
          <div class="">
            <div
              v-if="arrowOption.currentSlide !== onboardings.length - 1"
              class=""
            ></div>

            <div v-else>
              <v-btn block color="primary">Mulai</v-btn>
            </div>
          </div>
        </div>
      </template>
    </VueSlickCarousel>
  </div>
</template>
<script>
import SplashScreen from './SplashScreen.vue'
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'
export default {
  name: 'Onboarding',
  data() {
    return {
      slide: 0,
      getStartedButton: false,
      onboardings: [
        {
          subtitle: 'Mudah dan Cepat',
          text:
            '  Bayar Uang Kuliah Tunggal (UKT) dengan mudah kapan saja dan dimana saja.',
          imageUrl: require('../../public/img/onboarding1.png'),
        },
        {
          subtitle: 'Anti Ribet',
          text:
            '  Lewat beberapa klik, pembayaran UKT bisa selesai tanpa perlu ribet untuk mengantre .',
          imageUrl: require('../../public/img/onboarding2.png'),
        },
        {
          subtitle: 'Berbagai Metode Pembayaran',
          text:
            'Jelajahi berbagai metode pembayaran yang mudah dan terjamin keamananannya.',
          imageUrl: require('../../public/img/onboarding3.png'),
        },
      ],
      carousel: {
        dots: true,
        arrows: true,
        // fade: true,
        dotsClass: 'slick-dots custom-dot-class',
        edgeFriction: 0.35,
        infinite: false,
        speed: 500,
        slidesToShow: 1,
        slidesToScroll: 1,
        // variableWidth: true,
      },
    }
  },
  components: { SplashScreen },
}
</script>
<style scoped>
.center {
  margin: 0 auto !important;
}
</style>
