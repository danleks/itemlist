<template>
    <div class="itemWrapper">
        <div v-for="item in itemList" :key="item.id" class="item">
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
export default {
    data() {
        return {
            itemList: [],
        }
    },

    methods: {
        handleScroll(items) {
            let scrollHeight = window.scrollY;
            let maxHeight = window.document.body.scrollHeight - window.document.documentElement.clientHeight;

            if (scrollHeight >= maxHeight - 200) {
                this.getPosts(items);
            }
        },

        getPosts(items) {
            for (let i = 0; i < items.length; i++) {
                this.itemList.push({
                    id: items[i].id,
                    category: items[i].category,
                    price: items[i].price,
                    date: items[i].date,
                    description: items[i].description,
                    condition: items[i].condition,
                    url: items[i].url,
                })
            }
        }
    },

    created() {
        this.$root.$on('app-items', items => {
            this.itemList = items;
            // this.getPosts(items);
            //  window.addEventListener('scroll', this.handleScroll(items))
        });
       ;
    }

}
</script>

<style lang="scss" scoped>

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
