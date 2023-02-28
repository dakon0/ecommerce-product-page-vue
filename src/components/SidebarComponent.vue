<template>
    <div class="container" @click="$emit('sidebarBackgroundClicked')">
        <div class="sidebar" @click.stop>
            <div @click="$emit('closeSidebar')" class="close-sidebar"><img alt="close icon" :src="closeIcon" ></div>
            <div class="tabs">
                <div><a href="#collections">Collections</a></div>
                <div><a href="#men">Men</a></div>
                <div><a href="#women">Women</a></div>
                <div><a href="#about">About</a></div>
                <div><a href="#contact">Contact</a></div>
                
            </div>
        </div>
    </div>
</template>

<script setup>

import closeIcon from '/src/assets/images/icon-close.svg'

</script>

<style scoped lang="scss">
@keyframes containerOnSidebarAppearance {
    0% {background-color: rgba(0, 0, 0, 0);}
    100% {background-color: rgba(0, 0, 0, 0.8);}
}
@keyframes sidebarOnSidebarAppearance {
    0% {left: -250px;}
    100% {left: 0px;}
}
.container {
    display: flex;
    position: fixed;
    top: 0;
    left: 0px;
    z-index: 3;
    background-color: rgba(0, 0, 0, 0.8);
    animation: containerOnSidebarAppearance .5s;
    width: 100vw;
    height: 100vh;
}
    .sidebar {
        position: fixed;
        top: 0;
        left: 0px;
        z-index: 3;
        box-sizing: border-box;
        width: 250px;
        height: 100vh;
        background-color: white;
        animation: sidebarOnSidebarAppearance 0.5s;
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
    .close-sidebar:hover {
        img { content: url(../assets/images/icon-close-black.svg)};
        cursor: pointer;
    }

</style>