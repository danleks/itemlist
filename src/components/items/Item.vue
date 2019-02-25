<template>
    <div class="itemWrapper">
        <app-spinner v-if="load"></app-spinner>
        <div v-else v-for="item in itemsLoaded" :key="item.id" class="item">
            <figure class="item__img">
                <img :src="item.url" :alt="item.description">
            </figure>
            <div class="item__price">
                <span>$ {{item.price}}</span>
            </div>
            <div class="item__panel">
                <span>{{item.date}}</span>
                <span>{{item.description}}</span>
                <span>
                    <i v-for="star in item.condition" :key="star" class="fas fa-star"></i>
                </span>
            </div>
            <div class="item__more">
                <span>{{item.more}}</span>
            </div>
        </div>
    </div>
</template>

<script>
import Spinner from './Spinner.vue';

export default {
    data() {
        return {
            itemList: [],
            itemsLoaded: [],
            step: 0,
            load: true,
        }
    },

    components: {
        'app-spinner': Spinner,
    },

    methods: {
        handleScroll() {
            let scrollHeight = window.scrollY;
            let maxHeight = window.document.body.scrollHeight - window.document.documentElement.clientHeight;
            this.addPost(scrollHeight, maxHeight);
        },

        addPost(scrollHeight, maxHeight) {
            if (scrollHeight >= maxHeight - 50 && this.step < this.itemList.length) {
                for(let i = 0; i < 2; i++) {
                     this.itemsLoaded.push(this.itemList[this.step]);
                    this.step += 1;
                }

            }
        }
    },

    mounted() {
        this.$root.$on('app-items', items => {
                this.itemList = items;
        });

        setTimeout(()=>{
            this.load = false;
        }, 1000)

        this.addPost();
        window.addEventListener('scroll', this.handleScroll);
    }

}
</script>

<style lang="scss" scoped>
    .itemWrapper {
        margin: auto;
    }

    .item {
        position: relative;

        &__img {

            &:not(:last-child) {
                margin-bottom: 8px;
            }

            & > img {
                max-width: 100%;
            }
        }

        &__price {
            position: absolute;
            top: 1rem;
            left: 1rem;

            & > span {
                display: inline-block;
                padding: 6px 1.5rem;
                border-radius: 2px;
                font-size: 1.5rem;
                background-color: rgba(255,255,255, .8);
            }
        }

        &__panel {
            width: 100%;
            position: absolute;
            bottom: 3px;
            padding: 1.5rem;
            background-color: rgba(0,0,0,.5);

            & > span:nth-of-type(1) {
                display: block;
                width: 25%;
                color: #fff;
                font-size: 2rem;
                font-weight: bold;
            }

            & > span:nth-of-type(2) {
                display: block;
                width: 45%;
                color: #fff;
                font-size: 1.2rem;
            }

            & > span:nth-of-type(3) {
                position: absolute;
                top: 50%;
                right: 2%;
                transform: translateY(-50%);
                color: #fff;
            }
        }
    }

</style>
