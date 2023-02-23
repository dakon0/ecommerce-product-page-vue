<template>
    <div class="lightbox">
            <img class="main-image" alt="main image" :src=mainImagePath>
            <div class="other-images">
                <div class="chosen" @click="showFirstProduct"><img alt="first small image" src="../assets/images/image-product-1-thumbnail.jpg"></div>
                <div @click="showSecondProduct"><img alt="second small image" src="../assets/images/image-product-2-thumbnail.jpg"></div>
                <div @click="showThirdProduct"><img alt="third small image" src="../assets/images/image-product-3-thumbnail.jpg"></div>
                <div @click="showFourthProduct"><img alt="fouth small image" src="../assets/images/image-product-4-thumbnail.jpg"></div>
            </div>
        </div>
</template>

<script setup>
    import {ref} from 'vue'

    const mainImagePath = ref('./src/assets/images/image-product-1.jpg');

    function showFirstProduct(){
        mainImagePath.value = './src/assets/images/image-product-1.jpg';
    }

    function showSecondProduct(){
        mainImagePath.value = './src/assets/images/image-product-2.jpg';
    }

    function showThirdProduct(){
        mainImagePath.value = './src/assets/images/image-product-3.jpg';
    }

    function showFourthProduct(){
        mainImagePath.value = './src/assets/images/image-product-4.jpg';
    }

</script>

<style lang="scss" scoped>
    $orange: hsl(26, 100%, 55%);
    $pale-orange: hsl(25, 100%, 94%);
    $very-dark-blue: hsl(220, 13%, 13%);
    $dark-grayish-blue: hsl(219, 9%, 45%);
    $grayish-blue: hsl(220, 14%, 75%);
    $light-grayish-blue: hsl(223, 64%, 98%);
    $white: hsl(0, 0%, 100%);
    $black: hsl(0, 0%, 0%);
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
        img:hover {
            filter: opacity(30%);
        }
        div{
            width: 90px;
            height: 90px;
            border: solid 2px $white;
            border-radius: 12px;
        }
        .chosen {
            border: solid 2px $orange;
            border-radius: 12px;
            img {
                filter: opacity(30%);
            }
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
    }
</style>