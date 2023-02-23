<template>
  <header>
    <TopMenuBar/>
  </header>
  <main>
    <MainPartComponent/>
  </main>
</template>

<script setup>
// import HelloWorld from "./components/HelloWorld.vue";
  import TopMenuBar from "./components/TopManuBar.vue";
  import MainPartComponent from "./components/MainPartComponent.vue";
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Kumbh+Sans:wght@400;700&display=swap');
  #app {
    font-family: 'Kumbh Sans', sans-serif;
    font-size: 16px;
    /* background-color: black; */
    padding: 0px;
  }  
  body {
    margin: 0px;
  }
</style>
