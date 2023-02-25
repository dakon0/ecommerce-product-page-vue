<template>
  <header>
    <TopMenuBar/>
  </header>
  <main>
    <MainPartComponent @mainImageCliked2App="openPlayer"/>
  </main>
  <LightboxPlayer v-if="showPlayer" @playerCloseClicked="closePlayer" />
</template>

<script setup>
// import HelloWorld from "./components/HelloWorld.vue";
  import TopMenuBar from "./components/TopManuBar.vue";
  import MainPartComponent from "./components/MainPartComponent.vue";
  import LightboxPlayer from "./components/LightboxPlayer.vue";
  import {ref, onMounted} from 'vue'

  const showPlayer = ref(false);

  function closePlayer() {
    showPlayer.value = false;
  }

  function openPlayer() {
    showPlayer.value = true;
  }

  onMounted( () => window.addEventListener('resize', () => {
    if(innerWidth<450)closePlayer()
    }));
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Kumbh+Sans:wght@400;700&display=swap');
  #app {
    font-family: 'Kumbh Sans', sans-serif;
    font-size: 16px;
    padding: 0px;
  }  
  body {
    margin: 0px;
  }
</style>
