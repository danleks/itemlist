<template>
    <div class="details">
        <p>details</p>
        <a href="#" @click.prevent="closeDetails">close</a>
    </div>
</template>

<script>
export default {
    methods: {
        closeDetails() {
            this.$emit('closeDetails', false);
        }
    }
}
</script>

<style lang="scss" scoped>
    .details {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: #fff;
    }
</style>
