<template>
    <nav class="nav">
        <div class="nav__logo">
            <i class="fab fa-angellist"></i>
        </div>
        <div class="nav__buttons">
            <a class="button button--reg" href="#">login</a>
            <a class="button button--reg" href="#">sign in</a>
        </div>
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
        justify-content: space-between;
        align-items: center;
        padding: 0 1rem;

        @media(min-width: 768px) {
            grid-column: 1 / span 3;
        }

        &__logo {

            & > i {
                font-size: 2rem;
                color: #474747;
            }
        }

        &__buttons {

            & > *:not(:last-child) {
                margin-right: 4px;
            }
        }

    }
</style>
