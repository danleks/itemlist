<template>
    <div class="slides">
        <figure class="slides__img">
          <img :src="currentSlide.url" alt="">
        </figure>
        <slides-dots></slides-dots>
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
  .slides {
      position: relative;
      grid-column: 1 / span 2;
      width: 72vw;
      height: 72vw;
      border-radius: 50%;
      margin: auto;
      background-color: #fff;

      &__img {
        position: absolute;
        bottom: 1px;
        &> img {
          max-width: 100%;
        }
      }

  }
</style>
