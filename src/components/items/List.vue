<template>
    <section class="listWrapper">
        <app-filter></app-filter>
        <app-item></app-item>
    </section>
</template>

<script>
import Item from './Item.vue';
import Filter from './Filter.vue';

export default {
    data() {
        return {
            load: false,
        }
    },

    components: {
        'app-item': Item,
        'app-filter': Filter,
    },

    mounted() {
        setTimeout(()=>{
            this.load = true;
        }, 1000)
    }
}
</script>

<style lang="scss" scoped>
    .listWrapper {
        display: grid;
        grid-template-columns: 100%;
        grid-template-rows: 10rem auto;
        align-items: center;

        padding: 0 2rem;
    }

</style>
