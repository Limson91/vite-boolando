<script>
export default {

    data() {
        return {};
    },

    props: {
        card: Object
    },

    methods: {

        clickHeart() {
            this.card.isFavorite = !this.card.isFavorite;
        },

        returnDiscount() {
            for (let i = 0; i < this.card.badges.length; i++) {
                if (this.card.badges[i].type == 'discount') {
                    const discountValue = parseFloat(this.card.badges[i].value);
                    const finalPrice = (this.card.price * (100 + discountValue) / 100).toFixed(2);
                    return finalPrice;
                }
            }

            return this.card.price;
        }

        // showTag() {
        //     if (this.card.badges[0].type === 'tag') return
        // }
    }
}
</script>

<template>
    <div class="card">
        <figure>
            <img :src="card.frontImage" alt="" class="card-img" />
            <img :src="card.backImage" alt="" class="card-img-hover" />

            <div class="tags">
                <div :class="badge.type" v-for="badge in card.badges">{{ badge.value }}</div>
            </div>

            <div class="heart" @click="clickHeart()" :class="card.isFavorite ? 'heart-red' : ''">&hearts;</div>
        </figure>

        <div class="brand" @click="returnDiscount()">{{ card.brand }}</div>
        <div class="item">{{ card.name.toUpperCase() }}</div>

        <div class="price-container">
            <div class="discount-price">{{ returnDiscount() }} &euro;</div>
            <div class="price" v-show="card.price != returnDiscount()">{{ card.price }} &euro;</div>
        </div>
    </div>
</template>

<style scoped lang="scss">
@use '../style/partials/variables' as *;

.card {
    display: flex;
    flex-direction: column;

    figure {
        position: relative;

        .card-img-hover {
            display: none;
        }

        .tags {
            display: flex;
            gap: 5px;
            color: white;
            position: absolute;
            left: 0;
            bottom: 60px;
        }

        * {
            line-height: 24px;
        }

        .discount {
            background-color: $discount-color;
            order: -1;
            padding: 0 10px;
        }

        .tag {
            background-color: $tag-color;
            padding: 0 10px;
        }
    }

    &:hover {
        .card-img {
            display: none;
        }

        .card-img-hover {
            display: block;
        }
    }
}

.price-container {
    display: flex;
    gap: 10px;

    .discount-price {
        color: red;
        font-weight: 600;
    }

    .price {
        text-decoration: line-through;
    }

    .item {
        font-weight: 600;
    }
}

.heart {
    position: absolute;
    right: 0;
    top: 15px;
    background-color: white;
    aspect-ratio: 1;
    height: 40px;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    font-size: 25px;
}

.heart-red {
    color: red;
}
</style>