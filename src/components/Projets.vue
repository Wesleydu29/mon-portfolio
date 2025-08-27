<template>
    <div class="container">
        <div class="container-card">
            <ul>
                <li v-for="projet in projets" :key="projet.title" class="card">
                    <img :src="projet.imageUrl" :alt="projet.title">
                    <div class="infos-card">
                        <h2>{{ projet.title }}</h2>
                        <p>{{ projet.description }}</p>
                        <p>{{ projet.outils }}</p>
                    </div>
                </li>
            </ul>
        </div>
    </div>

</template>

<script setup>


import { ref } from 'vue';

const projets = ref([{
    imageUrl:'/images/chambre-hotel.jpg',
    title: "Hotel-connect",
    description:"Application mobile et internet de gestion d'hôtel",
    outils:"Javascript, React, PHP, Arduino"

}, {
    imageUrl:'/images/femme_souriante.webp',
    title: "Claude Henry, hypnothérapeute",
    description:"Création d'un site internet pour le compte d'un hypnothérapeute",
    outils:"Javascript, React, MongoDB, Nodejs et Express"

},{
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
    description:"Refonte d'un site internet pour le compte d'une photographe",
    outils:"HTML5, CSS3, Wave, SEO"

}, {
    imageUrl:'/images/m_v_g.jpg',
    title: "Mon vieux grimoire",
    description:"Mise en place d'un Back-end pour une application de location de livre",
    outils:"HTML5, CSS3, Javascript, Nodejs, Express, MongoDB"

}, {
    imageUrl:'/images/kasa.webp',
    title: "Kaza",
    description:"Création d'un site internet de location de bien immobilier",
    outils:"HTML5, SASS, Javascript, React"

}, {
    imageUrl:'/images/menu-maker.jpg',
    title: "Menu Maker",
    description:"Mise en situation, planification du développement d'un site web",
    outils:"Notion, veille technologique, Figma, AGILE"

}])
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  margin-top: 2em;
}

.container h2 {
  text-align: center;
  margin-bottom: 30px;
}

.container-card {
  width: 100%;
}

.container-card ul {
  display: flex;
  flex-wrap: wrap; 
  justify-content: center; 
  gap: 20px; 
  padding: 0;
  margin: 0;
}

.card {
  width: 29%;
  height: 550px;
  border-radius: 5px;
  border: 1px solid #ddd;
  list-style: none;
  display: flex;
  flex-direction: column;
  overflow: hidden; 
  transition: transform 0.5s;
}
.card:hover {
    transform: scale(1.05);
}
.card .infos-card {
    display: flex;
    flex-direction: column;
    height: 50%;
    gap: 20px;
    padding: 15px;
}

.card img {
  width: 100%;
  height: 50%;
  object-fit: cover; 
}

.card h2 {
  padding: 0 15px;
  margin: 15px 0 10px 0;
}



</style>