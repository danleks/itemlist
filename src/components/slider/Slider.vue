<template>
  <section class="slider" :style="{backgroundColor: currentSlide.activeBackground}">
    <div class="slider__innerContent">
      <app-menu></app-menu>
      <slider-indicator :currentSlide="currentSlide"></slider-indicator>
      <slider-claim></slider-claim>
      <app-slides :currentSlide="currentSlide"></app-slides>
    </div>
  </section>
</template>

<script>
import Menu from './Menu.vue';
import Indicator from './Indicator.vue';
import Claim from './Claim.vue';
import Slides from './Slides.vue';

export default {
  name: 'Slider',
  components: {
    'app-menu': Menu,
    'slider-indicator': Indicator,
    'slider-claim': Claim,
    'app-slides': Slides,

  },

  data() {
    return {
      details: false,
      currentSlide: {
        url: '',
        index: 0,
        id: 0,
        activeBackground: '',
        dotsBackground: '',
      },
    }
  },

  props: {
    slides: {
      type: Array,
      required: true,
    }
  },

  methods: {
    defaultSlide() {
      this.currentSlide.id = this.slides[0].id;
      this.currentSlide.url = this.slides[0].url;
      this.currentSlide.activeBackground = this.slides[0].bg;
      this.currentSlide.dotsBackground = this.slides[0].dots;
    },

    nextSlide() {
      let maxIndex = this.slides.length -1;
      let index = this.currentSlide.index < maxIndex ? this.currentSlide.index += 1 : this.currentSlide.index = 0;
      this.currentSlide.id = this.slides[index].id;
      this.currentSlide.url = this.slides[index].url;
      this.currentSlide.activeBackground = this.slides[index].bg;
      this.currentSlide.dotsBackground = this.slides[index].dots;
      this.$root.$emit('current-slide', this.currentSlide);
    },
  },

  created() {
    this.defaultSlide();
    this.$root.$emit('current-slide', this.currentSlide);
    setInterval( () => {
      this.nextSlide();
    }, 2500);

    this.$root.$on('showDetails', details => {
      this.details = details;
    });
    this.$root.$on('closeDetails', details => {
            this.details = details;
    });
  },
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

  .slider {

    &--active {
      background-color: var(--active-bg);
    }

    &__innerContent {
      display: grid;
      grid-template-columns: 9% auto;
      grid-template-rows: 8vh 30vh calc(100vh - 18vh - 30vh);
      grid-gap: 5vh;
      height: 100vh;
      max-width: 120rem;
      margin: auto;
      color: #474747;

      @media(min-width: 768px) {
        grid-template-columns: 6rem 40vw auto;
        grid-template-rows: 8vh 30vh;
        grid-gap: 1rem;
        grid-row-gap: 6rem;
        height: 54vh;
      }

      @media(min-width: 1024px) {
        grid-template-columns: 6rem 48% auto;
        grid-row-gap: 8rem;
        height: 70vh;
      }

      @media(min-width: 1200px) {
        grid-row-gap: 18rem;
        grid-template-columns: 6rem 55% auto;
        height: 100vh;
      }    }

  }
</style>
