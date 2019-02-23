<template>
     <div class="dotsBar">
        <div v-for="container in 4" :key="container" class="dotsBar__container">
            <span :style="{backgroundColor: dotsBackground}" v-for="dot in 8" :key="dot" class="dotsBar__item" />
        </div>
    </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
    .dotsBar {
        position: absolute;
        right: 0;

        &__container {
            &:not(:last-child) {
                margin-bottom: 2px;
            }
        }

        &__item {
            display: inline-block;
            width: 6px;
            height: 6px;
            border-radius: 50%;
            background-color: black;

            &:not(:last-child) {
                margin-right: 8px;
            }
        }
    }
</style>
