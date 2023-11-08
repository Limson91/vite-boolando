<script>
export default {
    // data() {
    //     return {
    //         cards: [
    //             {
    //                 img: '/1.webp',
    //                 imgHover: '1b.webp',
    //                 item: 'relaxed fit tee unisex',
    //                 brand: "Levi's",
    //                 discount: '50',
    //                 tag: 'Sostenibilità',
    //                 price: 29.99
    //             },
    //             {
    //                 img: '/2.webp',
    //                 imgHover: '2b.webp',
    //                 item: 'roses tee',
    //                 brand: "Guess",
    //                 discount: '30',
    //                 tag: '',
    //                 price: 29.99
    //             },
    //             {
    //                 img: '/3.webp',
    //                 imgHover: '3b.webp',
    //                 item: 'voglia di colori pastello',
    //                 brand: "Come Zucchero Filato",
    //                 discount: '30',
    //                 tag: '',
    //                 price: 129.99
    //             },
    //             {
    //                 img: '/4.webp',
    //                 imgHover: '4b.webp',
    //                 item: 'tee unisex',
    //                 brand: "Levi's",
    //                 discount: '50',
    //                 tag: '',
    //                 price: 29.99
    //             },
    //             {
    //                 img: '/5.webp',
    //                 imgHover: '5b.webp',
    //                 item: 'stripe bodice',
    //                 brand: "Maya Deluxe",
    //                 discount: '',
    //                 tag: '',
    //                 price: 99.99
    //             },
    //             {
    //                 img: '/6.webp',
    //                 imgHover: '6b.webp',
    //                 item: 'MAGLIONE - BLACK',
    //                 brand: "Espirit",
    //                 discount: '',
    //                 tag: 'Sostenibilità',
    //                 price: 29.99
    //             }
    //         ]
    //     }
    // },

    //     methods: {
    //         returnDiscountPrice(price, discount) {
    //             if (discount == '') return price;
    //             const percDiscount = parseFloat(discount) / 100;
    //             const discountPrice = (price * (1 - percDiscount)).toFixed(2);
    //             return discountPrice;
    //         }
    //     }
    // }

    data() {
        return {};
    },

    props: {
        card: Object
    },

    methods: {
        returnDiscountPrice(price, discount) {
            if (discount == "") return price;
            const percDiscount = parseFloat(discount) / 100;
            const discountPrice = (price * (1 - percDiscount)).toFixed(2);
            return discountPrice;
        },

        clickHeart() {
            this.card.like = !this.card.like;
        },

        showTag() {
            if (this.card.badges[0].type === 'tag') return
        }
    }
}
</script>

<template>
    <!-- <div class="container">
        <div class="row">
            <div class="col-4" v-for="card in cards">
                <div class="card">
                    <figure>
                        <img :src=card.img alt="" class="card-img">
                        <img :src=card.imgHover alt="" class="card-img-hover">

                        <div class="tags">
                            <div class="discount" v-show="card.discount != ''">-{{ card.discount }}%</div>
                            <div class="tag" v-show="card.tag != ''">{{ card.tag }}</div>
                        </div>

                        <div class="heart">&hearts;</div>
                    </figure>

                    <div class="brand">{{ card.brand }}</div>
                    <div class="item">{{ card.item.toUpperCase() }}</div>

                    <div class="price-container">
                        <div class="discount-price">{{ returnDiscountPrice(card.price, card.discount) }} &euro;</div>
                        <div class="price" v-show="card.discount != ''">{{ card.price }} &euro;</div>
                    </div>
                </div>
            </div>
        </div>
    </div> -->

    <div class="card">
        <figure>
            <img :src="card.frontImage" alt="" class="card_img">
            <img :src="card.backImage" alt="" class="card-img-hover">

            <div class="tags">
                <div class="discount" v-show="card.discount != ''">-{{ card.discount }}%</div>
                <div class="tag" v-show="card.tag != ''">{{ card.tag }}</div>
            </div>
            <div class="heart" @click="clickHeart()" :class="card.like ? 'heart-red' : ''">&hearts;</div>
        </figure>

        <div class="brand">{{ card.brand }}</div>
        <div class="item">{{ card.name }}</div>
        <div class="price-container">
            <div class="price" v-show="card.discount != ''">{{ card.price }} &euro;</div>
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
            padding: 0 10px;
        }

        .discont {
            background-color: $discount-color;
        }

        .tag {
            background-color: $tag-color;
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

    .discounted-price {
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
    font-size: 25px;
}

.heart-red {
    color: red;
}

// .row {
//     padding: 50px 0;
//     row-gap: 50px;
// }

// .heart {
//     position: absolute;
//     right: 0;
//     top: 15px;
//     background-color: white;
//     aspect-ratio: 1;
//     height: 40px;
//     display: flex;
//     justify-content: center;
//     align-items: center;
//     font-size: 25px;

//     &:hover {
//         color: red;
//     }
// }

// .heart-red {
//     color: red;
// }

// .card {
//     display: flex;
//     flex-direction: column;
//     margin-bottom: 20px;

//     figure {
//         position: relative;

//         .card-img-hover {
//             display: none;
//         }

//         .tags {
//             display: flex;
//             gap: 5px;
//             color: white;
//             position: absolute;
//             left: 0;
//             bottom: 60px;
//         }

//         * {
//             line-height: 24px;
//         }

//         .discount {
//             background-color: $discount-color;
//             padding: 0 10px;
//         }

//         .tag {
//             background-color: $tag-color;
//             padding: 0 10px;
//         }
//     }

//     &:hover {
//         .card-img {
//             display: none;
//         }

//         .card-img-hover {
//             display: block;
//         }
//     }
// }

// .price-container {
//     display: flex;
//     gap: 10px;

//     .discounted-price {
//         color: red;
//         padding: 10px;
//     }

//     .price {
//         text-decoration: line-through;
//     }
// }

// .item {
//     font-weight: 600;
// }
</style>