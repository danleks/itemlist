<template>
  <div id="app">
    <div class="mainWrapper">
      <app-slider :slides="slides"></app-slider>
    </div>
  </div>
</template>

<script>
import Slider from './components/Slider.vue';


export default {
  name: 'app',
  data() {
    return {
      slides: [
        {
          id: 1,
          name: 'bike',
          url: require('./assets/bike.png'),
          bg: '#c6eaf2',
          dots: '#afd5f3',
        },
        {
          id: 2,
          name: 'boat',
          url: require('./assets/boat.png'),
          bg: '#ffd9e5',
          dots: '#ffbdd6',

        },
        {
          id: 3,
          name: 'couch',
          url: require('./assets/couch.png'),
          bg: '#fcf77c',
          dots: '#fdda15',

        },
      ]
    }
  },

  components: {
    'app-slider': Slider,
  },

  mounted() {
    this.$root.$emit('app-slides', this.slides);
  }
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Rambla');
html {
  box-sizing: border-box;
  font-size: 62.5%;
}
*, *:before, *:after {
  box-sizing: inherit;
  padding: 0;
  margin: 0;
}

#app {
  font-family: 'Rambla', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.mainWrapper {
  position: relative;
}


// BUTTTON STYLES
.button {
  &,
  &:link,
  &:visited {
      border-radius: 4px;
      text-align: center;
      color: inherit;
      text-decoration: none;
  }

  &:hover {
    cursor: pointer;
  }

  &--primary {
    padding: .6rem 2.5rem;
    font-size: 1.3rem;
    background-color: #fff;

    @media(min-width: 768px) {
      font-size: 1.6rem;
    }

    @media(min-width: 1024px) {
      padding: 1rem 4rem;
    }
  }

  &--reg {
    padding: .6rem 1.5rem;
    font-size: 1.2rem;
    background-color: #fff;

     @media(min-width: 768px) {
      font-size: 1.4rem;
    }
  }
}
</style>
