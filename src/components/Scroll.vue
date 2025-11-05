<template>
    <transition name="fade">
        <button v-if="isVisible" @click="scrollToTop">
            Revenir en haut 
        </button>
    </transition>

</template>

<script setup>
import { ref, onMounted, onUnmounted  } from 'vue';

const isVisible = ref(false)

const handleScroll = () => {
    if (window.scrollY > 2000) {
            isVisible.value = true;
    } else {
            isVisible.value = false;
        }
}

const scrollToTop = () => {
    window.scrollTo({
            top: 0,
            behavior: 'smooth'
        });
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

</script>

<style scoped>
 button {
    width: 150px;
    height: 3.5rem;
    border-radius: 25px;
    border: none;
    font-size: 1rem;
    font-weight: bold;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    position: fixed;
    bottom: 30px;
    right: 30px;
    cursor: pointer;
    transition: opacity 0.3s ease;
 }
 .fade-enter-active, .fade-leave-active {
  transition: opacity 0.6s ease; 
}

.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
</style>