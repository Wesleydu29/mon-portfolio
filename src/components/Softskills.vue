<template>
    <Banner content="Softskills"/>
    <div class="container">
        <ul>
            <li v-for="item in softskills" :key="item.title" class="item">
                <img :src="item.image" :alt="item.title">
                {{ item.title }}
            </li>
        </ul>

    </div>

</template>

<script setup>
import { ref } from 'vue';

import Banner from './Banner.vue';

const softskills = ref([{
    title:"Javascript",
    image:"/icons/js.png"
}, {
    title:"React",
    image:"/icons/react.webp"
}, {
    title:"Vue.js",
    image:"/icons/vue.png"
}, {
    title:"Python",
    image:"/icons/python.png"
}, {
    title:"Base de données",
    image:"/icons/base-de-donnees.png"
}, {
    title:"Docker",
    image:"/icons/docker.png"
}, {
    title:"Jenkins",
    image:"/icons/Jenkins_logo.png"
}])
</script>

<style scoped>
.container {
  width: 100%;
  margin-top: 4rem;
}

ul {
  list-style: none;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  width: 100%;
  padding: 0;
  margin: 0;
}

.item {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-size: 2rem;
  flex: 1;
  min-width: 0;
  padding: 10px;
}

img {
  width: 100px;
  margin-bottom: 8px;
}
</style>