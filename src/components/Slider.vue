<template>
  <section class="slider">
    <app-menu></app-menu>
    <div class="slider__indicatorList">
      <span v-for="slider in sliders" :key="slider.id" class="slider__indicator"></span>
      <span class="line" />
      <span class="text">warsaw, poland</span>
    </div>
    <div class="claim">
      <h1>buy.sell.trade</h1>
      <div class="claim__content">
        <h3>Community driven</h3>
        <p>We are classified advertisements website with sections devoted to jobs, housing, personals, for sale, items wanted, services, community, gigs, resumes, and discussion forums.</p>
      </div>
      <a class="button button--primary" href="#">learn more</a>
    </div>
    <div class="slider__content">
      <div class="circle">
        <figure class="circle__img">
          <img src="../assets/bike.png" alt="">
      </figure>
      </div>
    </div>
  </section>
</template>

<script>
import Menu from './Menu.vue';

export default {
  name: 'Slider',
  components: {
    'app-menu': Menu,
  },
  props: {
    sliders: {
      type: Array,
      required: true,
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  .slider {
    display: grid;
    grid-template-columns: 9% auto;
    grid-template-rows: 10% 20rem auto;
    grid-gap: 5%;
    height: 100vh;
    width: 100%;
    color: #474747;
    background-color: #c6eaf2;

    &__indicatorList {
      display: flex;
      flex-direction: column;
      align-items: center;

      .line {
        width: 4rem;
        height: 1px;
        margin-top: 3rem;
        transform: rotate(90deg);
        background-color: #474747;
      }

      .text {
        width: 7rem;
        margin-top: 6rem;
        transform: rotate(-90deg);

      }
    }

    &__indicator {
      display: block;
      width: 1rem;
      height: 1rem;
      border-radius: 50%;
      margin-bottom: .7rem;
      background-color: #fff;
    }





    &__content {
      grid-column: 1 / span 2;
      display: flex;
      flex-direction: column;
      align-items: center;

      & > .circle {
        position: relative;
        width: 25rem;
        height: 25rem;
        border-radius: 50%;
        background-color: #fff;
      }

      .circle__img {
        position: absolute;
        bottom: 1%;
      }
    }
  }

  .claim {
    display: flex;
    flex-direction: column;

    & > h1 {
      font-size: 3.2rem;
      margin-bottom: 2rem;
    }

    & > &__content {
      width: 90%;
      margin-bottom: 2rem;

      & > h3 {
        font-size: 1.8rem;
        margin-bottom: .6rem;
      }

      & > p {
        font-size: 1.4rem;
      }
    }

    & > a {
       align-self: flex-start;
    }
  }



  img {
    width: 250px;
    height: 140px;;
  }
</style>
