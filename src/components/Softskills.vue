<template>
 <Banner content="Soft skills"/>
    <div class="container">
        <div class="slider-wrapper" ref="sliderWrapper">
            <div class="slider" ref="slider">
            <!-- items originaux -->
                <div v-for="item in softskills" :key="`original-${item.title}`" class="item">
                    <img :src="item.image" :alt="item.title">
                    <span>{{ item.title }}</span>
                </div>
                <!-- duplicata afin de gérer la fluidité du slider -->
                <div v-for="item in softskills" :key="`clone-${item.title}`" class="item">
                    <img :src="item.image" :alt="item.title">
                    <span>{{ item.title }}</span>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted, nextTick } from 'vue';
import Banner from './Banner.vue';

const slider = ref(null);
const sliderWrapper = ref(null);
let animationId = null;
let currentPosition = 0;
const speed = 2; // pixels par frame
let isPaused = false;
let itemsWidth = 0;

const softskills = ref([{
title:"HTML5",
image:"/icons/html5.png"
},{
title:"CSS3",
image:"/icons/css3.png"
},{
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
title:"Django",
image:"/icons/django-logo.png"
}, {
title:"Kivy",
image:"/icons/Kivy_logo.png"
},{
title:"Base de données",
image:"/icons/base-de-donnees.png"
},{
title:"Docker",
image:"/icons/docker.png"
}, {
title:"Jenkins",
image:"/icons/Jenkins_logo.png"
}]);

const calculateItemsWidth = () => {
if (slider.value) {
const items = slider.value.querySelectorAll('.item');
if (items.length > 0) {
// Calcule de la largeur totale des items originaux
itemsWidth = 0;
const originalItems = Math.floor(items.length / 2);
for (let i = 0; i < originalItems; i++) {
  const itemRect = items[i].getBoundingClientRect();
  const computedStyle = window.getComputedStyle(items[i]);
  const marginLeft = parseFloat(computedStyle.marginLeft);
  const marginRight = parseFloat(computedStyle.marginRight);
  itemsWidth += itemRect.width + marginLeft + marginRight;
}
}
}
};

const animate = () => {
if (!isPaused && slider.value && itemsWidth > 0) {
currentPosition -= speed;

// quand on a parcouru la largeur des items originaux,
// on revient au début de façon seamless
if (Math.abs(currentPosition) >= itemsWidth) {
  currentPosition = 0;
}

slider.value.style.transform = `translateX(${currentPosition}px)`;
}

animationId = requestAnimationFrame(animate);
};

const handleMouseEnter = () => {
isPaused = true;
};

const handleMouseLeave = () => {
isPaused = false;
};

onMounted(async () => {
await nextTick();
  
// Attendre que les images soient chargées pour calculer les dimensions
const images = slider.value?.querySelectorAll('img') || [];
const imagePromises = Array.from(images).map(img => {
if (img.complete) return Promise.resolve();
return new Promise(resolve => {
  img.onload = resolve;
  img.onerror = resolve;
});
});

await Promise.all(imagePromises);
  
// calcul des dimensions et démarrage de l'animation
setTimeout(() => {
calculateItemsWidth();
animate();
}, 100);

// Ajouter les événements hover
if (sliderWrapper.value) {
sliderWrapper.value.addEventListener('mouseenter', handleMouseEnter);
sliderWrapper.value.addEventListener('mouseleave', handleMouseLeave);
}

// Recalculer si la fenêtre change de taille
window.addEventListener('resize', calculateItemsWidth);
});

onUnmounted(() => {
if (animationId) {
cancelAnimationFrame(animationId);
}

if (sliderWrapper.value) {
sliderWrapper.value.removeEventListener('mouseenter', handleMouseEnter);
sliderWrapper.value.removeEventListener('mouseleave', handleMouseLeave);
}

window.removeEventListener('resize', calculateItemsWidth);
});
</script>

<style scoped>
.container {
width: 100%;
margin-top: 4rem;
overflow: hidden;
margin-bottom: 4rem;
}

.slider-wrapper {
width: 100%;
overflow: hidden;
position: relative;
}

.slider {
display: flex;
width: fit-content;
will-change: transform; /* Optimisation GPU */
}

.item {
display: flex;
flex-direction: column;
align-items: center;
justify-content: center;
font-size: 1.5rem;
font-weight: 600;
min-width: 200px;
padding: 20px;
margin: 0 20px;
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
border-radius: 15px;
color: white;
text-align: center;
box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
transition: transform 0.3s ease, box-shadow 0.3s ease;
flex-shrink: 0;
}

.item:hover {
transform: translateY(-5px);
box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
}

.item img {
width: 80px;
height: 80px;
margin-bottom: 15px;
filter: brightness(1.1);
object-fit: contain;
background: rgba(255, 255, 255, 0.1);
padding: 10px;
border-radius: 50%;
}

.item span {
text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
font-family: 'poppins', sans-serif;
}


@media (max-width: 768px) {
.item {
min-width: 150px;
font-size: 1.2rem;
padding: 15px;
margin: 0 10px;
}

.item img {
width: 60px;
height: 60px;
margin-bottom: 10px;
}
}

@media (max-width: 480px) {
.item {
min-width: 120px;
font-size: 1rem;
padding: 10px;
}

.item img {
width: 50px;
height: 50px;
}
}
</style>