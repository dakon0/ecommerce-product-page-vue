<template>
    <div class="info-controls">
        <div class="info">
            <h5>SNEAKER COMPANY</h5>
            <h1>Fall Limited Edition Sneakers</h1>
            <p>These low-profile sneakers are your perfect casual wear companion. Featuring a durable rubber outer sole, they'll withstand everything the weather can offer.</p>
            <div class="price-discount-prev">
                <div class="price-discount">
                    <div class="price">$125.00</div>
                    <div class="discount">50%</div>
                </div>
                <div class="prev-price">$250.00</div>
            </div>
        </div>
        <div class="controls">
            <div class="counter">
                <div @click="minusClicked" class="decrement"><img alt="minus-sign" src="../assets/images/icon-minus.svg"></div>
                <div class="order-number">{{ orderNumber }}</div>
                <div @click="plusClicked" class="increment"><img alt="plus-sign" src="../assets/images/icon-plus.svg"></div>
            </div>
            <div @click="addToCartClicked" class="add-to-chart-btn">
                <img alt="white cart" src="../assets/images/icon-cart-white.svg">
                <span>Add to cart</span>
            </div>
        </div>
    </div>
</template>

<script setup>
    import {ref} from 'vue'
    const emit = defineEmits(['addToCartClicked']);
    const orderNumber = ref(0);
    function minusClicked() {
        if(orderNumber.value > 0) orderNumber.value--;
    }
    function plusClicked() {
        orderNumber.value++;
    }
    function addToCartClicked() {
        if(orderNumber.value > 0) {
            emit('addToCartClicked', orderNumber.value);
            orderNumber.value = 0;
        }
    }
</script>

<style scoped lang="scss">
    .info-controls {
        width: 450px;
    }
    .info {
        h5 {
            color: $orange;
            letter-spacing: 2px;
            margin-top: 60px;
        }
        h1 {
            font-size: 44px;
            color: $black;
        }
        p{
            color: $dark-grayish-blue;
            line-height: 25px;
        }
    }
    .price-discount {
        display: flex;
        align-items: center;
        margin-bottom: 10px;
        .price {
            font-size: 32px;
            font-weight: 700;
            margin-right: 15px;
        }
        .discount {
            color: $orange;
            background-color: $pale-orange;
            padding: 2px 5px;
            font-weight: 700;
            border-radius: 5px;
        }
    }
    .prev-price {
        color: $grayish-blue;
        font-weight: 700;
        margin-bottom: 30px;
        text-decoration: line-through;
    }
    .controls{
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 50px;
        .counter{
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-weight: 700;
            background-color: $light-grayish-blue;
            box-sizing: border-box;
            padding: 10px;
            width: 155px;
            height: 50px;
            border-radius: 7px;
            .decrement{
                padding-bottom: 8px;
            }
            .decrement:hover, .increment:hover{
                filter: opacity(30%);
                cursor: pointer;
            }

        }
        .add-to-chart-btn{
            display: flex;
            justify-content:center;
            box-sizing: border-box;
            width: 270px;
            height: 50px;
            padding: 16px 10px 12px;
            border-radius: 7px;
            background-color: $orange;
            color: $white;
            font-weight: 700;
            font-size: 14px;
            box-shadow: 0px 30px 15px $pale-orange;
            img {
                width: 15px;
                height: 15px;
                margin-right: 10px;
            }
        }
        .add-to-chart-btn:hover {
            filter: opacity(70%);
            cursor: pointer;
        }
    }
    @media (max-width: 450px) {
        .info{
            h5 {
                margin: 0px 0px 18px 0px;
                font-size: 12px;
            }
            h1 {font-size: 28px;}
        }
        .info-controls{
            width: calc(100vw - 50px);
        }
        .controls{
            flex-direction: column;
            .counter, .add-to-chart-btn{
                width: 100%;
            }
            .counter{margin-bottom: 15px;}
        }
        .price-discount-prev {
            display: flex;
            align-items: center;
            justify-content: space-between;
            .prev-price{ margin: 0 0 10px 0; }
        }
    }
    @media (max-width: 300px) {
        .price-discount-prev {
            flex-direction: column;
            align-items: flex-start;
        }
        .price-discount {
            flex-direction: column;
            align-items: flex-start;
        }
    }
</style>