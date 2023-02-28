<template>
    <div class="cart-container">
        <div class="title"><span>Cart</span></div>
        <div v-if="cartIsNotEmpty">
            <div class="order-info">
                <div class="item-image"><img alt="ordered item image" :src="orderedItemImage"></div>
                <div class="description-number-price">
                    <div class="item-description">{{ itemDescription }}</div>
                    <div class="number-price">${{ price }}.00 x {{ orderedNumber }} <span class="total-price">${{ totalPrice }}.00</span></div>
                </div>
                <div @click="$emit('deleteIconClicked')" @mouseover="deleteIconSrc = deleteIconBlack" @mouseout="deleteIconSrc = deleteIconGrey" class="delete-order"><img alt="delete button icon" :src="deleteIconSrc"></div>
            </div>
            <div class="checkout-btn">Checkout</div>
        </div>
        <div v-else class="empty-cart-content">Your cart is empty.</div>
    </div>
</template>

<script setup>
import orderedItemImage from '/src/assets/images/image-product-1-thumbnail.jpg'
import deleteIconGrey from '/src/assets/images/icon-delete.svg'
import deleteIconBlack from '/src/assets/images/icon-delete-black.svg'

import {ref, computed} from 'vue'

const props = defineProps({
    orderedNumber: {required: true, type: Number}
})

const deleteIconSrc = ref(deleteIconGrey)
const itemDescription = ref('Fall Limited Edtion Sneakers');
const price = ref(125.0);

const totalPrice = computed(() => price.value * props.orderedNumber);

const cartIsNotEmpty = computed(() => props.orderedNumber > 0 ? true : false);

</script>

<style scoped lang="scss">
    .cart-container {
        width: 350px;
        border: solid transparent 1px;
        padding: 25px 0;
        background-color: $white;
        border-radius: 12px;
        box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.2);
        .title {
            padding-bottom: 25px;
            padding-left: 20px;
            border-bottom: solid 2px $grayish-blue;
            font-weight: 700;
        }
        .order-info {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin: 20px;
        }
    }
    .item-image {
        height: 50px;
        img {
            width: 50px;
            border-radius: 5px;
        }
    }
    .delete-order img:hover {
        // content: url(../assets/images/icon-delete-black.svg);
        cursor: pointer;
    }
    .description-number-price{
        color: $dark-grayish-blue;
        .item-description {
            margin-bottom: 5px;
        }
        .number-price {
            margin-bottom: 5px;
        }
        .total-price{
            color: $very-dark-blue;
            font-weight: 700;
        }
    }
    .checkout-btn {
        box-sizing: border-box;
        height: 55px;
        margin: 0px 20px;
        padding-top: 16px;
        border-radius: 10px;
        background-color: $orange;
        color: $white;
        font-weight: 700;
        text-align: center;
    }
    .checkout-btn:hover {
        filter: opacity(70%);
        cursor: pointer;
    }
    .empty-cart-content {
        box-sizing: border-box;
        height: 145px;
        text-align: center;
        color: $dark-grayish-blue;
        font-weight: 700;
        font-size: 15px;
        padding-top: 70px;
    }
    @media(max-width: 352px) {
        .cart-container{
            // width: 300px;
            width: calc(100vw - 2px);
            .title {
                padding-left: 5px;
            }
            .order-info {
                margin: 20px 5px;
            }
            .checkout-btn {
                margin: 0px 5px;
            }
        }
    }
</style>