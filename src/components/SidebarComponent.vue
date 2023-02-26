<template>
    <div class="sidebar">
        <div @click="$emit('closeSidebar')" class="close-sidebar"><img alt="close icon" :src="closeIcon" ></div>
        <div class="tabs">
            <div>Collections</div>
            <div>Men</div>
            <div>Women</div>
            <div>About</div>
            <div>Contact</div>
        </div>
    </div>
</template>

<script setup>

import closeIcon from '/src/assets/images/icon-close.svg'

</script>

<style scoped lang="scss">
    .sidebar {
        box-sizing: border-box;
        width: 250px;
        height: 100vh;
        position: fixed;
        z-index: 3;
        top: 0;
        left: 0;
        background-color: white;
        .close-sidebar {
            margin: 20px 0px 50px 20px;
        }
        .tabs div {
            font-weight: 700;
            padding: 10px 0px 10px 20px;
        }
        .tabs div:hover {
            background-color: $grayish-blue;
        }
    }


    .close-sidebar:hover {
        img { content: url(../assets/images/icon-close-black.svg)}
    }

</style>