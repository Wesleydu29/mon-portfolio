<template>
    <Header/>
    <Home/>

    <Footer/>
  
</template>

<script setup> 

import Header from './components/Header.vue'
import Footer from './components/Footer.vue';
import Home from './Pages/Home.vue'
</script>
<style scoped>
* {
    padding: 30px;
    font-family: 'poppins', sans-serif;
}
</style>