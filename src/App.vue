<template>
  <div id="app">
    <div class="mainWrapper">
      <app-slider :slides="slides"></app-slider>
      <app-list></app-list>
    </div>
  </div>
</template>

<script>
import Slider from './components/slider/Slider.vue';
import List from './components/items/List.vue';


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
      ],

      items: [
        {
          id: 11,
          category: 'couch',
          price: 300,
          date: 'Dec 20',
          description: 'hardly used sectional',
          condition: 3,
          url: require('./assets/couches/couch-1.jpg'),
        },
        {
          id: 12,
          category: 'couch',
          price: 150,
          date: 'Jan 02',
          description: 'sectional great condition',
          condition: 4,
          url: require('./assets/couches/couch-2.jpg'),
        },
        {
          id: 13,
          category: 'couch',
          price: 275,
          date: 'Sept 15',
          description: 'leather sectional like new',
          condition: 3,
          url: require('./assets/couches/couch-3.jpg'),
        },
        {
          id: 14,
          category: 'couch',
          price: 360,
          date: 'May 11',
          description: 'pier one couch',
          condition: 2,
          url: require('./assets/couches/couch-4.jpg'),
        },
        {
          id: 15,
          category: 'couch',
          price: 455,
          date: 'Jun 03',
          description: 'mint condition couch',
          condition: 3,
          url: require('./assets/couches/couch-5.jpeg'),
        },
        {
          id: 16,
          category: 'couch',
          price: 580,
          date: 'July 14',
          description: 'urban outfitters couch',
          condition: 3,
          url: require('./assets/couches/couch-6.jpg'),
        },
        {
          id: 17,
          category: 'couch',
          price: 133,
          date: 'April 22',
          description: 'rooms to go sectional',
          condition: 3,
          url: require('./assets/couches/couch-7.jpeg'),
        },
      ]
    }
  },

  components: {
    'app-slider': Slider,
    'app-list': List,
  },

  mounted() {
    this.$root.$emit('app-slides', this.slides);
    this.$root.$emit('app-items', this.items);
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
    width: 15rem;
    padding: .6rem 2.5rem;
    font-size: 1.3rem;
    background-color: #fff;

    @media(min-width: 768px) {
      font-size: 1.6rem;
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
