<template>
  <section class="slider">
    <div class="slider__innerContent">
      <app-menu></app-menu>
      <slider-indicator :currentSlide="currentSlide"></slider-indicator>
      <slider-claim></slider-claim>
      <app-slides></app-slides>
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
      currentSlide: {
        url: null,
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
    },
  },

  created() {
    this.defaultSlide();   
    setInterval( () => {
      this.nextSlide();
    }, 2500)
  },
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .slider {
    background-color: #c6eaf2;

    &__innerContent {
      display: grid;
      grid-template-columns: 9% auto;
      grid-template-rows: 8% 20rem auto;
      grid-gap: 5%;
      height: 100vh;
      max-width: 120rem;
      margin: auto;
      color: #474747;      

      @media(min-width: 768px) {
        grid-template-columns: 9% 40% auto;
        height: 60vh;
      }

      @media(min-width: 1024px) {
        grid-template-rows: 10% auto;
        grid-gap: unset;
        grid-row-gap: 10%;
      }
    }

    &__content {
      position: relative;
      grid-column: 1 / span 2;
      display: flex;
      flex-direction: column;
      align-items: center;

       @media(min-width: 1024px) {
         grid-column: unset;
       }

      & > .circle {
        position: relative;
        width: 25rem;
        height: 25rem;
        border-radius: 50%;
        background-color: #fff;

         @media(min-width: 768px) {
          width: 28rem;
          height: 28rem;
        }

        @media(min-width: 1024px) {
          position: absolute;
          top: -1.1rem;
          width: 42rem;
          height: 42rem;
        }
      }

      .circle__img {
        position: absolute;
        bottom: 1%;
      }

      .dots {
          position: absolute;
          right: -3rem;

          @media(min-width: 1024px) {
              right: -5rem;
              top: 4rem;
          }

          &__container {
            margin-bottom: 2px;

            @media(min-width: 768px) {
              margin-bottom: 5px;
            }

          }

          &__item {
            display: inline-block;
            width: 6px;
            height: 6px;
            border-radius: 50%;
            margin-right: 8px;
            background-color: #AFD5F3;

            @media(min-width: 768px) {
              width: 8px;
              height: 8px;
              margin-right: 12px;
            }

            @media(min-width: 1024px) {
              width: 1rem;
              height: 1rem;
              margin-right: 1.4rem;
              margin-bottom: 4px;
            }
          }
      }
    }
  }

  .claim {
    display: flex;
    flex-direction: column;

    & > h1 {
      font-size: 3.2rem;
      margin-bottom: 2rem;

      @media(min-width: 768px) {
        font-size: 5rem;
      }

      @media(min-width: 1024px) {
        font-size: 8rem;
        letter-spacing: .7rem;
        z-index: 1;
      }
    }

    & > &__content {
      width: 90%;
      margin-bottom: 2rem;

       @media(min-width: 768px) {
          width: 55%;
        }

        @media(min-width: 1024px) {
          width: 100%;
        }

      & > h3 {
        font-size: 1.8rem;
        margin-bottom: .6rem;

        @media(min-width: 768px) {
          font-size: 2.3rem;
        }

        @media(min-width: 1024px) {
          letter-spacing: 2px;
        }
      }

      & > p {
        font-size: 1.4rem;

        @media(min-width: 1024px) {
          line-height: 1.5;
        }
      }
    }

    & > a {
       align-self: flex-start;
    }
  }



  img {
    width: 250px;
    height: 150px;

    @media(min-width: 768px) {
      width: 250px;
      height: 150px;
    }

    @media(min-width: 1024px) {
      width: 450px;
      height: 250px;
    }
  }
</style>
