<template>
    <nav class="nav">
        <span>itemslist</span>
        <a class="button button--reg" href="#">login</a>
        <a class="button button--reg" href="#">sign in</a>
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

        @media(min-width: 1024px) {
            grid-column: 1 / span 3;
        }

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
