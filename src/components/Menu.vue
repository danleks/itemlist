<template>
    <nav class="nav">
        <span>itemslist</span>
        <a class="button button--primary" href="#">login</a>
        <a class="button button--primary" href="#">sign in</a>
    </nav>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
    .nav {
        grid-column: 1 / span 2;
        display: flex;
        align-items: center;

        & > span {
            flex: 2;
            margin-left: 6px;
            font-size: 1.8rem;

        }

        & > a {
            margin-right: 6px;
        }

    }
</style>
