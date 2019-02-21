<template>
    <div class="indicatorList">
      <span v-for="indicator in slidesFORindicators" :key="indicator.id" :class="[indicator.id === currentSlide.id ? styles.activeIndicator : '', styles.indicator]" />
      <span class="indicatorList__line" />
      <span class="indicatorList__text">warsaw, poland</span>
    </div>
</template>

<script>
export default {
  data() {
    return {
      slidesFORindicators: 0,
      styles: {
        indicator: 'indicatorList__indicator',
        activeIndicator: 'indicatorList__indicator--active',
      }
    }
  },

  props: {
    currentSlide: {
      type: Object,
      required: true,
    }
  },

  mounted() {
    this.$root.$on('app-slides', slides => {
      this.slidesFORindicators = slides;
    })    
  }

}
</script>

<style lang="scss" scoped>
  .indicatorList {
    display: flex;
    flex-direction: column;
    align-items: center;

    &__indicator {
      display: block;
      width: 1rem;
      height: 1rem;
      border-radius: 50%;
      margin-bottom: 7px;
      background-color: #fff;

      &--active {
        background-color: #474747;
      }
    }

    &__line {
        width: 4rem;
        height: 1px;
        margin-top: 3rem;
        transform: rotate(90deg);
        background-color: #474747;
    }

    &__text {
        width: 7rem;
        margin-top: 6rem;
        transform: rotate(-90deg);
    }
  }
</style>
