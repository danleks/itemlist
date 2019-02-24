<template>
    <section class="filter">
        <div class="filter__header">
            <a href="#">filter</a>
            <i class="fas fa-sort"></i>
        </div>
    </section>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
    .filter {

        background-color: rgba(0,0,0,.1);

        &__header {
            padding: 2rem 0;
            position: relative;
            text-align: center;

            & > a {
                &,
                &:link,
                &:visited {
                    display: inline-block;
                    padding: 1rem 4rem;
                    border-radius: 4px;
                    font-size: 2rem;
                    letter-spacing: 4px;
                    color: #fff;
                    text-decoration: none;
                    background-color: rgba(0,0,0, .5);
                }
            }

            & > i {
                position: absolute;
                right: 2rem;
                top: 50%;
                transform: translateY(-50%);
                color: rgba(0, 0, 0, .8);
                font-size: 3rem;
                cursor: pointer;
            }
        }
    }
</style>
