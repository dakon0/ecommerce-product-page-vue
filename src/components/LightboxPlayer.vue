<template>
    <div @click="$emit('playerCloseClicked')" class="background">
        <div @click.stop class="player">
            <div @click="$emit('playerCloseClicked')" class="close-btn"><img alt="close button image" :src="closeBtnWhiteIcon"></div>
            <div class="main-image"><img alt="main image" :src=mainImagePath></div>
            <div class="other-images">
                <div :class="{ chosen: chosenProductImage === 1 }" @click="showFirstProduct"><img alt="first small image" :src=thumbnail_1><div class="overlay"></div></div>
                <div :class="{ chosen: chosenProductImage === 2 }" @click="showSecondProduct"><img alt="second small image" :src=thumbnail_2><div class="overlay"></div></div>
                <div :class="{ chosen: chosenProductImage === 3 }" @click="showThirdProduct"><img alt="third small image" :src=thumbnail_3><div class="overlay"></div></div>
                <div :class="{ chosen: chosenProductImage === 4 }" @click="showFourthProduct"><img alt="fouth small image" :src=thumbnail_4><div class="overlay"></div></div>
            </div>
            <div class="navigation">
                <div @click="previousClicked" class="previous-btn"><img alt="prev arrow image" :src="prevArrow"></div>
                <div class="placeholder"></div>
                <div @click="nextClicked" class="next-btn"><img alt="next arrow image" :src="nextArrow"></div>
            </div>
        </div>
    </div>
</template>

<script setup>
    import {ref} from 'vue'
    import closeBtnWhiteIcon from '../assets/images/icon-close-white.svg'
    import thumbnail_1 from '/src/assets/images/image-product-1-thumbnail.jpg'
    import thumbnail_2 from '/src/assets/images/image-product-2-thumbnail.jpg'
    import thumbnail_3 from '/src/assets/images/image-product-3-thumbnail.jpg'
    import thumbnail_4 from '/src/assets/images/image-product-4-thumbnail.jpg'
    import product_1 from '/src/assets/images/image-product-1.jpg'
    import product_2 from '/src/assets/images/image-product-2.jpg'
    import product_3 from '/src/assets/images/image-product-3.jpg'
    import product_4 from '/src/assets/images/image-product-4.jpg'
    import prevArrow from '/src/assets/images/icon-previous.svg'
    import nextArrow from '/src/assets/images/icon-next.svg'


    const mainImagePath = ref(product_1);
    const chosenProductImage = ref(1);

    function showFirstProduct(){
        mainImagePath.value = product_1;
        chosenProductImage.value = 1;
    }

    function showSecondProduct(){
        mainImagePath.value = product_2;
        chosenProductImage.value = 2;
    }

    function showThirdProduct(){
        mainImagePath.value = product_3;
        chosenProductImage.value = 3;

    }

    function showFourthProduct(){
        mainImagePath.value = product_4;
        chosenProductImage.value = 4;
    }

    function previousClicked(){
        if(chosenProductImage.value === 1){
            mainImagePath.value = product_4;
            chosenProductImage.value = 4;
        }
        else if(chosenProductImage.value === 2){
            mainImagePath.value = product_1;
            chosenProductImage.value = 1;
        }
        else if(chosenProductImage.value === 3){
            mainImagePath.value = product_2;
            chosenProductImage.value = 2;
        }
        else if(chosenProductImage.value === 4){
            mainImagePath.value = product_3;
            chosenProductImage.value = 3;
        }
    }

    function nextClicked(){
        if(chosenProductImage.value === 1){
            mainImagePath.value = product_2;
            chosenProductImage.value = 2;
        }
        else if(chosenProductImage.value === 2){
            mainImagePath.value = product_3;
            chosenProductImage.value = 3;
        }
        else if(chosenProductImage.value === 3){
            mainImagePath.value = product_4;
            chosenProductImage.value = 4;
        }
        else if(chosenProductImage.value === 4){
            mainImagePath.value = product_1;
            chosenProductImage.value = 1;
        }
    }

</script>

<style scoped lang="scss">
    .background {
        position: fixed;
        z-index: 4;
        top: 0px;
        width: 100vw;
        height: 100vh;
        background-color: rgba(0, 0, 0, 0.7);
        overflow: auto;
    }
    .player {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 604px;
        height: 740px;
        border: 3px solid transparent;
        margin: 75px auto;
        .close-btn {
            align-self: flex-end;
            img { width: 22px;}
            margin: 0px 25px 20px 0px;
        }
        .close-btn:hover {
            img {content: url(../assets/images/icon-close-orange.svg); }
            cursor: pointer;
        }
        .main-image {
            margin-bottom: 35px;
            img {
                width: 550px;
                border-radius: 15px;
            }
        }
        .navigation {
            display: flex;
            position: relative;
            top: -450px;
            div {
                box-sizing: border-box;
                width: 55px;
                height: 55px;
                border-radius: 40px;
                background-color: $white;
            }
            .previous-btn {
                padding: 18.5px 0px 0px 19px;
            }
            .next-btn {
                padding: 18.5px 0px 0px 23px;
            }
            .previous-btn:hover {
                img {content: url(../assets/images/icon-previous-orange.svg); }
                cursor: pointer;
            }
            .next-btn:hover{
                img {content: url(../assets/images/icon-next-orange.svg); }
                cursor: pointer;
            }
            .placeholder {
                background-color: transparent;
                width: 494px;
            }
        }
        .other-images {
            display: flex;
            justify-content: space-evenly;
            width: 520px;
            img {
                width: 90px;
                border-radius: 9px;
            }
            div{
                width: 90px;
                height: 90px;
                border: solid 2px transparent;
                border-radius: 12px;
            }
            div .overlay {
                position: relative;
                top: -94px;
            }
            div:hover {
                .overlay {
                    width: 90px;
                    height: 90px;
                    border: none;
                    border-radius: 9px;
                    position: relative;
                    top: -94px;
                    background-color: rgba(255, 255, 255, 0.4);
                    cursor: pointer;
                }
            }
            .chosen {
                border: solid 3px $orange;
                border-radius: 12px;
                .overlay {
                    width: 90px;
                    height: 90px;
                    border: none;
                    border-radius: 9px;
                    position: relative;
                    top: -94px;
                    background-color: rgba(255, 255, 255, 0.7);
                }
            }
            .chosen:hover {
                cursor: pointer;
                .overlay {
                    background-color: rgba(255, 255, 255, 0.7);
                }
            }
        } 
    }
    @media(max-height: 815px) {
        .player{
            margin: calc(50vh - 310px) auto;
            height: 620px;
            .other-images{
                display: none;
            }
            .navigation{
                top: -350px;
            }
        }
    }
    @media(max-height: 640px) {
        .player{
            width: 450px;
            height: 500px;
            margin: calc(50vh - 250px) auto;
            .main-image img{
                width: 450px;
            }
            .other-images {
                justify-content:space-evenly;
                width: 450px;
            }
            .navigation{
                top: -300px;
                .placeholder{
                    width: 340px;
                }
            }
        }
    }
    @media(max-width: 610px) {
        .player{
            width: 450px;
            height: 500px;
            margin: calc(50vh - 250px) auto;
            .main-image img{
                width: 450px;
            }
            .other-images {
                justify-content:space-evenly;
                width: 450px;
                display: none;
            }
            .navigation{
                top: -300px;
                .placeholder{
                    width: 340px;
                }
            }
        }
    }
    @media(max-width: 450px) { 
        .background {
            display: none;
        }
    }


</style>