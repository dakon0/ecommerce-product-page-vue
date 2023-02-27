<template>
    <div class="container">
        <div class="sidebar">
            <div @click="$emit('closeSidebar')" class="close-sidebar"><img alt="close icon" :src="closeIcon" ></div>
            <div class="tabs">
                <div><a href="#collections">Collections</a></div>
                <div><a href="#men">Men</a></div>
                <div><a href="#women">Women</a></div>
                <div><a href="#about">About</a></div>
                <div><a href="#contact">Contact</a></div>
                
            </div>
        </div>
        <div @click="$emit('sidebarBackgroundClicked')" class="background"></div>
    </div>
</template>

<script setup>

import closeIcon from '/src/assets/images/icon-close.svg'

</script>

<style scoped lang="scss">
.container {
    display: flex;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 3;
}
    .sidebar {
        box-sizing: border-box;
        width: 250px;
        height: 100vh;


        background-color: white;
        .close-sidebar {
            margin: 20px 0px 50px 20px;
            width: 15px;
        }
        .tabs div {
            // padding: 10px 0px 10px 20px;
            margin: 10px 0px 10px 0px;
            a {
                padding: 5px 80% 5px 20px;
                font-weight: 700;
                color: $very-dark-blue;
                text-decoration: none;
            }
        }
        .tabs div:hover {
            background-color: $grayish-blue;
            cursor: pointer;
        }
    }
    .background {
        height: 100vh;
        width: calc(100vw - 250px);
        background-color: rgba(0, 0, 0, 0.8);
    }

    .close-sidebar:hover {
        img { content: url(../assets/images/icon-close-black.svg)};
        cursor: pointer;
    }

</style>