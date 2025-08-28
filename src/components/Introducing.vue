<template>
  <div class="container" ref="containerRef">
    <div class="introducing" :class="{ 'visible': isVisible }">
      <p class="typewriter-text">
        {{ displayedText }}
        <span class="cursor" v-show="showCursor">|</span>
      </p>
      <img 
        src="/images/profil.jpg" 
        alt="portrait Wesley Goarant" 
        class="profile-image" 
        :class="{ 'fade-in': isVisible }"
      >
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const containerRef = ref(null)
const displayedText = ref('')
const isVisible = ref(false)
const showCursor = ref(true)

const fullText = "Je m'appelle Wesley, j'ai 25ans et depuis quelques années maintenant je me suis découvert une nouvelle passion, le développement web, plus précisément le développement front-end, avec des bases en back-end. Je suis actuellement à la recherche d'une alternance pour la rentrée 2025 à compter de septembre, pour un bachelor IT developpeur full stack. Alors si vous passez par là et que mon profil vous intéresse, n'hésitez pas à me contacter pour discuter davantage."

const typingSpeed = 30
let typingInterval = null
let observer = null

// fonction de frappe
const startTyping = () => {
  displayedText.value = ''
  let currentIndex = 0
  
  typingInterval = setInterval(() => {
    if (currentIndex < fullText.length) {
      displayedText.value = fullText.substring(0, currentIndex + 1)
      currentIndex++
    } else {
      clearInterval(typingInterval)
      // masque le curseur après 3secondes
      setTimeout(() => {
        showCursor.value = false
      }, 3000)
    }
  }, typingSpeed)
}

// Configuration de l'observer
onMounted(() => {
  if (!containerRef.value) return
  
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting && !isVisible.value) {
          isVisible.value = true
          // délai avant de commencer à écrire
          setTimeout(startTyping, 500)
        }
      })
    },
    {
      threshold: 0.3,
      rootMargin: '0px 0px -50px 0px' // Se déclenche un peu avant
    }
  )
  
  observer.observe(containerRef.value)
})

// Nettoyage
onUnmounted(() => {
  if (typingInterval) {
    clearInterval(typingInterval)
  }
  if (observer) {
    observer.disconnect()
  }
})
</script>

<style scoped>
.container {
  margin-top: 2rem;
  background-color: rgba(201, 202, 217, 0.2);
  padding: 20px;
}

.introducing {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 100px;
  opacity: 0;
  transform: translateY(30px);
  transition: all 0.8s ease-out;
}

.introducing.visible {
  opacity: 1;
  transform: translateY(0);
}

.typewriter-text {
  width: 30%;
  font-size: 1.2rem;
  font-family: 'Poppins', sans-serif;
  line-height: 1.2;
  min-height: 200px;
}

.cursor {
  color: #2c3e50;
  font-weight: bold;
  animation: blink 1s infinite;
}

@keyframes blink {
  0%, 50% { 
    opacity: 1; 
  }
  51%, 100% { 
    opacity: 0; 
  }
}

.profile-image {
  width: 300px;
  height: auto;
  opacity: 0;
  transform: translateX(30px) scale(0.95);
  transition: all 1s ease-out 0.3s;
}

.profile-image.fade-in {
  opacity: 1;
  transform: translateX(0) scale(1);
}


@media (max-width: 1024px) {
  .introducing {
    gap: 50px;
  }
  
  .typewriter-text {
    width: 40%;
  }
  
  .profile-image {
    width: 250px;
  }
}

@media (max-width: 768px) {
  .introducing {
    flex-direction: column;
    gap: 30px;
    text-align: center;
  }
  
  .typewriter-text {
    width: 90%;
  }
  
  .profile-image {
    width: 200px;
    transform: translateY(20px) scale(0.95);
  }
  
  .profile-image.fade-in {
    transform: translateY(0) scale(1);
  }
}

@media (max-width: 480px) {
  .container {
    padding: 15px;
  }
  
  .typewriter-text {
    font-size: 1rem;
    width: 95%;
  }
  
  .profile-image {
    width: 180px;
  }
}
</style>