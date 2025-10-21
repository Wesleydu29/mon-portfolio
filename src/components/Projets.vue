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
                        <p>Outils :</p>
                        <div class="outils">
                            <img 
                            v-for="outil in projet.outils" 
                            :key="outil.name"
                            :src="outil.icon" 
                            :alt="outil.name"
                            class="outil-icon"
                            >
                        </div>
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
    imageUrl:'/images/bg1.jpg',
    title: "GALAXY",
    description:"Jeu mobile et desktop en 2D avec perspective, le but étant de rester sur le chemin tracé, sans jamais en sortir",
    outils:[
      { name: "Python", icon: "/icons/python.png" },
      { name: "Kivy", icon: "/icons/Kivy_logo.png" }
    ],
    link:"https://github.com/Wesleydu29/Galaxy_Game"


},{
    imageUrl:'/images/chambre-hotel.jpg',
    title: "Hotel-connect",
    description:"Application mobile et internet de gestion d'hôtel",
    outils:[
      { name: "Javascript", icon: "/icons/js.png" },
      { name: "PHP", icon: "/icons/PHP.png" },
      { name: "React", icon: "/icons/react.webp" }
    ]

}, {
    imageUrl:'/images/femme_souriante.webp',
    title: "Claude Henry, hypnothérapeute",
    description:"Création d'un site internet pour le compte d'un hypnothérapeute",
    outils:[
      { name: "Javascript", icon: "/icons/js.png" },
      { name: "React", icon: "/icons/react.webp" },
      { name: "Mongodb", icon: "/icons/mongodb.png" },
      { name: "Nodejs", icon: "/icons/Node.js.png" },
      { name: "Express", icon: "/icons/Expressjs.png" }
    ],
    name:"Javascript, React, MongoDB, Nodejs et Express",
    link:"https://github.com/Wesleydu29/Claude_Henry"

},{
    imageUrl:'/images/appartement-paris-v.png',
    title: "Sophie Bluel",
    description:"Conception d'un site internet pour le compte d'une architecte",
    outils:[
      { name: "Javascript", icon: "/icons/js.png" },
      { name: "HTML", icon: "/icons/html5.png" },
      { name: "CSS", icon: "/icons/css3.png" }
    ],
    link:"https://github.com/Wesleydu29/Projet-3"

}, {
    imageUrl:'/images/booki.jpg',
    title: "Booki",
    description:"Conception d'un site internet de réservation de vacance",
    outils:[
      { name: "HTML", icon: "/icons/html5.png" },
      { name: "CSS", icon: "/icons/css3.png" }
    ],
    link:"https://github.com/Wesleydu29/projet2"

}, {
    imageUrl:'/images/nina_carducci.webp',
    title: "Nina Carducci",
    description:"Refonte d'un site internet pour le compte d'une photographe",
    outils:[
      { name: "HTML", icon: "/icons/html5.png" },
      { name: "CSS", icon: "/icons/css3.png" },
      { name: "Wave", icon: "/icons/wave-logo.jpg" },
      { name: "SEO", icon: "/icons/SEO.jpg" }
    ],
    link:"https://github.com/Wesleydu29/projet-4"

}, {
    imageUrl:'/images/m_v_g.jpg',
    title: "Mon vieux grimoire",
    description:"Mise en place d'un Back-end pour une application de location de livre",
    outils:[
      { name: "HTML", icon: "/icons/html5.png" },
      { name: "CSS", icon: "/icons/css3.png" },
      { name: "Javascript", icon: "/icons/js.png" },
      { name: "Nodejs", icon: "/icons/Node.js.png" },
      { name: "Express", icon: "/icons/Expressjs.png" },
      { name: "MongoDB", icon: "/icons/mongodb.png" }
    ],
    link:"https://github.com/Wesleydu29/P6_mon_vieux_grimoire"

}, {
    imageUrl:'/images/kasa.webp',
    title: "Kasa",
    description:"Création d'un site internet de location de bien immobilier",
    outils:"HTML5, SASS, Javascript, React",
    outils:[
      { name: "HTML", icon: "/icons/html5.png" },
      { name: "SASS", icon: "/icons/Sass.png" },
      { name: "Javascript", icon: "/icons/js.png" },
      { name: "React", icon: "/icons/react.webp" },
    ],
    link:"https://github.com/Wesleydu29/P5-Kasa"

}, {
    imageUrl:'/images/menu-maker.jpg',
    title: "Menu Maker",
    description:"Mise en situation, planification du développement d'un site web, gestion agile",
    outils:[
      { name: "Notion", icon: "/icons/icon-notion.png" },
      { name: "Figma", icon: "/icons/Figma-logo.svg" },
      { name: "Javascript", icon: "/icons/js.png" },
    ],

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
    align-items: center;
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
  display: block; 
  aspect-ratio: 16 / 9;
}

.card h2 {
  padding: 0 15px;
  margin: 15px 0 10px 0;
}
.outils {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 10px;
}
.outils .outil-icon {
  width: 65px;
  height: 65px;
  object-fit: contain;
  filter: brightness(1.1);
  transition: transform 0.3s ease, filter 0.3s ease;
}

.outil-icon:hover {
  transform: scale(1.2);
  filter: brightness(1.3);
}
</style>