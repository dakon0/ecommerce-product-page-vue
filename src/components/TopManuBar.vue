<template>
    <div class="container">
        <div class="logo-menu">
            <div @click="$emit('openMenuIconClicked')" class="menu-btn"><img alt="menu button icon" src="../assets/images/icon-menu.svg"></div>
            <div class="sneakers-logo"><img alt="sneakers logo" src="../assets/images/logo.svg"></div>
            <div class="menu">
                <div class="Collections"><a href="#collections">Collections</a></div>
                <div class="Men"><a href="#men">Men</a></div>
                <div class="Women"><a href="#women">Women</a></div>
                <div class="About"><a href="#about">About</a></div>
                <div class="Contact"><a href="#contact">Contact</a></div>
            </div>
        </div>
        <div class="cart-profile">
            <CartComponent v-if="showCart" @click.stop @deleteIconClicked="$emit('deleteIconClicked')" :orderedNumber="orderedNumber" class="cart-component" />
            <div @click.stop="$emit('cartIconClicked')" class="cart"><img alt="cart-icon" src="../assets/images/icon-cart.svg"></div>
            <div v-if="orderedNumber > 0" class="notifications"><span>{{ orderedNumber }}</span></div>
            <div class="profile"><img alt="profile-photo" src="../assets/images/image-avatar.png"></div>
        </div>
    </div>
</template>

<script setup>
    import CartComponent from "./CartComponent.vue"
    import {ref} from 'vue'
    const props = defineProps({
        orderedNumber: {required: true, type: Number},
        showCart: {required: true, type: Boolean}
    })
</script>

<style lang="scss" scoped>
    .container {
        display: flex;
        align-items: start;

        justify-content: space-between;
        margin: 30px 160px 0px;
        border-bottom: $grayish-blue 2px solid;
    }
    .logo-menu {
        display: flex;
        padding-top: 15px;
        // height: 70px;
    }
    .menu-btn {
        padding-top: 3px;
        margin-right: 15px;
        display: none;
    }
    .menu {
        display: flex;
        font-weight: 400;
        margin-left: 50px;

        div {
            margin-right: 30px;
            padding-bottom: 40px;
            a {
                text-decoration: none;
                color: $dark-grayish-blue;
                padding-bottom: 40px;

            }
        }
    }
    .menu{
        a:hover {
            color: $black;
            border-bottom: solid 4px $orange;
            padding-bottom: 36px;
            cursor: pointer;
        }
    }
    .cart-profile {
        position: relative;
        display: flex;
        align-items: center;
    }
    .cart:hover {
        img {content:url(../assets/images/icon-cart-black.svg);}
        cursor: pointer;
    }
    .notifications {
        width: 17px;
        height: 11px;
        border-radius: 7px;
        position: absolute;
        left: 10px;
        top: 13px;
        background-color: $orange;
        font-size: 9px;
        text-align: center;
        font-weight: 700;
        color: $white;
    }
    .profile {
        margin-left: 40px;
        img {
            width: 47px;
            border-radius: 30px;
            border: solid 3px $white;
        }
    }
    .profile:hover {
        img{
            border-radius: 30px;
            border: solid 3px $orange;
            cursor: pointer;
        }
    }
    @keyframes cart-animation {
        0%   {top:-280px;}
        50%  {top:80px;}
        100% {top:60px;}
    }
    .cart-component {
        position: absolute;
        z-index: 1;
        left: -140px;
        top: 60px;
        animation-name: cart-animation;
        animation-duration: .5s;

    }
    @media(max-width: 1100px) {
        .container {
            margin: 30px 30px 0px;
        }
        .cart-component {
        left: -250px;
    }
    }
    @media(max-width: 800px) {
        .menu{ display: none;}
        .menu-btn {display: unset;}
    }
    @media(max-width: 450px) {
        .container{
            border: none;
            margin-top: 20px;
            padding-bottom: 20px;
            align-items: center;
        }
        .logo-menu {
            padding: 0px;
        }
        .sneakers-logo {
            img {height: 20px;}
        }
        .profile {
            margin-left: 20px;
            img {
                width: 24px;
            }
        }
        .notifications{
            top: 1px;
        }
        .cart-component {
            left: calc(-1 * 50vw + 102px - 176px);//centering cart box 102 is width of offset cart image and profile photo are giving and 176 is half of a cart box width 
        }
    }
    @media(max-width: 352px) {
        .cart-component{
            left: calc(-1 * 50vw + 102px - 50vw);
        }
    }
    @media(max-width: 300px) {
        .container {
            margin: 30px 0px 0px;
            .profile { margin: 0px; }
        }
        .cart-component{
            left: calc(-1 * 50vw + 52px - 50vw);
        }
    }
</style>
