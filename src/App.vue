<template @click="hideCart">
  <header>
    <TopMenuBar @cartIconClicked="toggleCartDisplay" @openMenuIconClicked="() => sidebarDisplayed = true" @deleteIconClicked="() => orderedNumber = 0" :orderedNumber="orderedNumber" :showCart="showCart"/>
  </header>
  <main>
    <MainPartComponent @mainImageCliked2App="openPlayer" @addToCartClicked="actualizeCart" />
  </main>
  <LightboxPlayer v-if="showPlayer" @playerCloseClicked="closePlayer" class="lightbox-player"/>
  <SidebarComponent v-if="sidebarDisplayed" @sidebarBackgroundClicked="sidebarDisplayed=false" @closeSidebar="sidebarDisplayed = false"/>
</template>

<script setup>
  import TopMenuBar from "./components/TopManuBar.vue";
  import MainPartComponent from "./components/MainPartComponent.vue";
  import LightboxPlayer from "./components/LightboxPlayer.vue";
  import SidebarComponent from "./components/SidebarComponent.vue";
  import {ref, onMounted} from 'vue'

  const showPlayer = ref(false);

  function closePlayer() {
    showPlayer.value = false;
  }

  function openPlayer() {
    showPlayer.value = true;
  }
  
  onMounted( () => window.addEventListener('resize', () => {
    if(innerWidth<450)closePlayer();
    if(innerWidth>800) sidebarDisplayed.value = false;
  }));
  
  const orderedNumber = ref(0);
  function actualizeCart(valueToAdd){
    orderedNumber.value += valueToAdd;
  }

  const sidebarDisplayed = ref(false)

  const showCart = ref(false);
  function toggleCartDisplay() {
    showCart.value = !showCart.value;
  }
  function hideCart(){
    showCart.value = false;
  }
  const app = document.getElementById('app');
  app.addEventListener('click', hideCart);
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Kumbh+Sans:wght@400;700&display=swap');
  #app {
    font-family: 'Kumbh Sans', sans-serif;
    font-size: 16px;
    padding: 0px;
  }  
  body {
    margin: 0px;
  }
  @keyframes onLightboxPlayerAppearance{
    0% {opacity: 0%;}
    100% {opacity: 100%;}
  }

  .lightbox-player {
    opacity: 100%;
    animation: onLightboxPlayerAppearance .5s;
  }
</style>
