<template>
     <div class="dotsBar">
        <div v-for="container in 4" :key="container" class="dotsBar__container">
            <span :style="{backgroundColor: dotBg}" v-for="dot in 8" :key="dot" class="dotsBar__item" />
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            dotBg: '#afd5f3',
        }
    },

    created() {
        this.$root.$on('current-slide', currentSlide => {
            this.dotBg = currentSlide.dotsBackground;
        })
  }

}
</script>

<style lang="scss" scoped>
    .dotsBar {
        position: absolute;
        right: 0;

        @media(min-width: 1200px) {
            right: -2%;
            top: 4%;
        }

        &__container {
            &:not(:last-child) {
                margin-bottom: 2px;

                @media(min-width: 768px) {
                    margin-bottom: 6px;
                }

                @media(min-width: 1200px) {
                    margin-bottom: 8px;
                }
            }
        }

        &__item {
            display: inline-block;
            width: 6px;
            height: 6px;
            border-radius: 50%;

            @media(min-width: 768px) {
                width: 8px;
                height: 8px;
            }

            @media(min-width: 768px) {
                width: 1.2rem;
                height: 1.2rem;
            }

            &:not(:last-child) {
                margin-right: 8px;

                @media(min-width: 768px) {
                    margin-right: 1.2rem;
                }

                @media(min-width: 1200px) {
                    margin-right: 1.6rem;
                }
            }
        }
    }
</style>
