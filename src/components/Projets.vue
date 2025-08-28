<template>
    <div class="container">
        <div class="container-card">
            <ul>
                <li v-for="projet in projets" :key="projet.title" class="card">
                    <a :href="projet.link " target="_blank" class="card-link">
                    <img :src="projet.imageUrl" :alt="projet.title">
                    <div class="card-content">
                        <h2>{{ projet.title }}</h2>
                        <p>{{ projet.description }}</p>
                        <p>{{ projet.outils }}</p>
                    </div>
                    </a>
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
    outils:"Javascript, React, MongoDB, Nodejs et Express",
    link:"https://github.com/Wesleydu29/Claude_Henry"

},{
    imageUrl:'/images/appartement-paris-v.png',
    title: "Sophie Bluel",
    description:"Conception d'un site internet pour le compte d'une architecte",
    outils:"HTML5, CSS3, Javascript",
    link:"https://github.com/Wesleydu29/Projet-3"

}, {
    imageUrl:'/images/booki.jpg',
    title: "Booki",
    description:"Conception d'un site internet de réservation de vacance",
    outils:"HTML5, CSS3",
    link:"https://github.com/Wesleydu29/projet2"

}, {
    imageUrl:'/images/nina_carducci.webp',
    title: "Nina Carducci",
    description:"Refonte d'un site internet pour le compte d'une photographe",
    outils:"HTML5, CSS3, Wave, SEO",
    link:"https://github.com/Wesleydu29/projet-4"

}, {
    imageUrl:'/images/m_v_g.jpg',
    title: "Mon vieux grimoire",
    description:"Mise en place d'un Back-end pour une application de location de livre",
    outils:"HTML5, CSS3, Javascript, Nodejs, Express, MongoDB",
    link:"https://github.com/Wesleydu29/P6_mon_vieux_grimoire"

}, {
    imageUrl:'/images/kasa.webp',
    title: "Kasa",
    description:"Création d'un site internet de location de bien immobilier",
    outils:"HTML5, SASS, Javascript, React",
    link:"https://github.com/Wesleydu29/P5-Kasa"

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
  font-family: 'poppins', sans-serif;
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
    box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
}
.card-link,
.card-content {
    display: flex;
    flex-direction: column;
    height: 100%;
    text-decoration: none;
    color: #000;
}
.card-content {
    padding: 15px;
    font-family: 'poppins', sans-serif;
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