<template>
    <div class="container">
        <LightboxComponent @mainImageClicked2MainPart="$emit('mainImageCliked2App')"/>
        <InfoAndOrder @addToCartClicked="(orderNumber) => $emit('addToCartClicked', orderNumber)"/>
    </div>
</template>

<script setup>
    import LightboxComponent from './LightboxComponent.vue';
    import InfoAndOrder from './InfoAndOrder.vue'
</script>

<style lang="scss" scoped>
    .container{
        display: flex;
        justify-content: space-between;
        margin: 75px 210px 0px 210px;
    }
    @media (max-width: 1300px) {
        .container {
            margin: 75px 100px 0px;
        }
    }
    @media (min-width: 1600px) {
        .container {
            justify-content: space-around;
        }
    }
    @media (max-width: 1100px) {
        .container {
            margin: 75px 10px 0px;
        }
    }
    @media (max-width: 950px) {
        .container {
            flex-direction: column;
            align-items: center;
        }
    }
    @media (max-width: 450px) {
        .container {
            margin: 0px;
        }
    }

    

</style>