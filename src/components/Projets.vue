<template>
    <div class="container">
        <h2>Mes projets</h2>
        <div class="container-card">
            <ul>
                <li v-for="projet in projets" :key="projet.title" class="card">
                    <img :src="projet.imageUrl" :alt="projet.title">
                    <h2>{{ projet.title }}</h2>
                    <p>{{ projet.description }}</p>
                </li>
            </ul>

        </div>

    </div>

</template>

<script setup>

import { ref } from 'vue';

const projets = ref([{
    imageUrl:'/images/appartement-paris-v.png',
    title: "Sophie Bluel",
    description:"Conception d'un site internet pour le compte d'une architecte",
    outils:"HTML5, CSS3, Javascript"

}, {
    imageUrl:'/images/booki.jpg',
    title: "Booki",
    description:"Conception d'un site internet de réservation de vacance",
    outils:"HTML5, CSS3"

}, {
    imageUrl:'/images/nina_carducci.webp',
    title: "Nina Carducci",
    description:"Conception d'un site internet pour le compte d'une architecte"

}, {
    imageUrl:'/images/appartement-paris-v.png',
    title: "Sophie Bluel",
    description:"Conception d'un site internet pour le compte d'une architecte"

}])
</script>

<style scoped>
.card {
    width: 300px;
    height: auto;
}
li {
    list-style: none;
}
li img {
    width: 100%;
    height: 33%;
}

</style>