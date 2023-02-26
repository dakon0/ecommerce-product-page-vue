<template>
    <div class="lightbox">
            <img @click="mainImageClicked" class="main-image" alt="main image" :src=mainImagePath>
            <div class="other-images">
                <div :class="{ chosen: chosenProductImage === 1 }" @click="showFirstProduct"><img alt="first small image" :src=thumbnail_1><div class="overlay"></div></div>
                <div :class="{ chosen: chosenProductImage === 2 }" @click="showSecondProduct"><img alt="second small image" :src=thumbnail_2><div class="overlay"></div></div>
                <div :class="{ chosen: chosenProductImage === 3 }" @click="showThirdProduct"><img alt="third small image" :src=thumbnail_3><div class="overlay"></div></div>
                <div :class="{ chosen: chosenProductImage === 4 }" @click="showFourthProduct"><img alt="fouth small image" :src=thumbnail_4><div class="overlay"></div></div>
            </div>
            <div class="navigation">
                <div @click="previousClicked" class="previous-btn"><img alt="prev arrow image" :src="prevArrow"></div>
                <div @click="nextClicked" class="next-btn"><img alt="next arrow image" :src="nextArrow"></div>
            </div>
        </div>
</template>

<script setup>
    import {ref} from 'vue'
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

    // const windowWidth = ref(window.innerWidth)
    const emit = defineEmits(['mainImageClicked2MainPart']);
    function mainImageClicked() {
        if(innerWidth > 450) emit('mainImageClicked2MainPart');
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

<style lang="scss" scoped>
    .main-image {
        margin-bottom: 20px;
        width: 450px;
        border-radius: 15px; 
    }
    .other-images {
        display: flex;
        justify-content: space-between;
        width: 450px;
        img {
            width: 90px;
            border-radius: 10px;
        }
        div{
            width: 90px;
            height: 90px;
            border: solid 2px $white;
            border-radius: 12px;
        }
        .overlay {
                width: 90px;
                height: 90px;
                border: none;
                border-radius: 10px;
                position: relative;
                top: -94px;
            }
        div:hover {
            .overlay {
                background-color: rgba(255, 255, 255, 0.3);
            }
        }
        .chosen {
            border: solid 3px $orange;
            border-radius: 12px;
            .overlay {
                background-color: rgba(255, 255, 255, 0.7);
            }
        }
        .chosen:hover {
            .overlay {
                background-color: rgba(255, 255, 255, 0.7);

            }
        }
    }
    .navigation {
        display: none;
        width: 100vw;
        justify-content: space-between;
        position: absolute;
        top: 200px;
        div {
                box-sizing: border-box;
                width: 45px;
                height: 45px;
                border-radius: 40px;
                background-color: $white;
                margin: 0px 20px;
            }
            .previous-btn {
                padding: 13.5px 0px 0px 15px;
            }
            .next-btn {
                padding: 13.5px 0px 0px 18px;
            }
            .previous-btn:hover {
                img {content: url(../assets/images/icon-previous-orange.svg); }
            }
            .next-btn:hover{
                img {content: url(../assets/images/icon-next-orange.svg); }
            }
    }
    @media (max-width: 450px) {
        .main-image{
                width: 100vw;
                height: 300px;
                border-radius: 0;
                object-fit: cover;
            }
        .other-images {
            display: none;
        }
        .navigation {
            display: flex;
        }
    }
</style>