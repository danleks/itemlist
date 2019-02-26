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
            details: false,
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

        this.$root.$on('showDetails', details => {
            this.details = details;
        });
        this.$root.$on('closeDetails', details => {
            this.details = details;
        });
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
