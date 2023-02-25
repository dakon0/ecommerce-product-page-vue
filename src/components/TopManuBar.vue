<template>
    <div class="container">
        <div class="logo-menu">
            <div class="menu-btn"><img alt="menu button icon" src="../assets/images/icon-menu.svg"></div>
            <div class="sneakers-logo"><img alt="sneakers logo" src="../assets/images/logo.svg"></div>
            <div class="menu">
                <div class="Collections">Collections</div>
                <div class="Men">Men</div>
                <div class="Women">Women</div>
                <div class="About">About</div>
                <div class="Contact">Contact</div>
            </div>
        </div>
        <div class="cart-profile">
            <div class="cart"><img alt="cart-icon" src="../assets/images/icon-cart.svg"></div>
            <div class="profile"><img alt="profile-photo" src="../assets/images/image-avatar.png"></div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
    $orange: hsl(26, 100%, 55%);
    $pale-orange: hsl(25, 100%, 94%);
    $very-dark-blue: hsl(220, 13%, 13%);
    $dark-grayish-blue: hsl(219, 9%, 45%);
    $grayish-blue: hsl(220, 14%, 75%);
    $light-grayish-blue: hsl(223, 64%, 98%);
    $white: hsl(0, 0%, 100%);
    $black: hsl(0, 0%, 0%);
    .container {
        display: flex;
        align-items: start;

        justify-content: space-between;
        margin: 30px 160px 0px;
        // padding-bottom: 30px;
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
        color: $dark-grayish-blue;
        div {
            margin-right: 30px;
            padding-bottom: 40px;
        }
    }
    .menu{
        div:hover {
            color: $black;
            border-bottom: solid 4px $orange;
            padding-bottom: 36px;
        }
    }
    .cart-profile {
        display: flex;
        align-items: center;
    }
    .cart:hover {
        img {content:url(../assets/images/icon-cart-black.svg);}
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
            border: solid 3px $orange
        }
    }
    @media(max-width: 1100px) {
        .container {
            margin: 30px 30px 0px;
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
    }
    @media(max-width: 300px) {
        .container {
            margin: 30px 0px 0px;
            .profile { margin: 0px; }
        }
    }
</style>
