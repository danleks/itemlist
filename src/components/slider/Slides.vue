<template>
    <div class="slidesWrapper">
      <div class="slides">
          <figure class="slides__img">
            <img :src="currentSlide.url" alt="">
          </figure>
          <slides-dots></slides-dots>
      </div>
    </div>
</template>

<script>
import Dots from './Dots.vue';

export default {
  components: {
    'slides-dots': Dots,
  },

  props: {
    currentSlide: {
      type: Object,
      required: true,
    }
  }
}
</script>

<style lang="scss" scoped>
  .slidesWrapper {
    position: relative;
    grid-column: 1 / span 2;
    margin: auto;

    @media(min-width: 768px) {
      grid-column: unset;
      width: 100%;
      height: 100%;
    }
  }
  .slides {
      position: relative;
      width: 45vh;
      height: 45vh;
      border-radius: 50%;
      background-color: #fff;

      @media(min-width: 768px) {
        position: absolute;
        top: -10%;
        width: 47vw;
        height: 47vw;
      }

      @media(min-width: 1024px) {
        top: -20%;
        width: 40rem;
        height: 40rem;
      }

      @media(min-width: 1200px) {
        top: -35%;
        width: 50rem;
        height: 50rem;
      }

      &__img {
        position: absolute;
        bottom: 1px;
        height: 70%;

        &> img {
          max-width: 100%;
        }
      }

  }
</style>
