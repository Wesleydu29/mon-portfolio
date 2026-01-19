<template>
    <div class="container" @click="toggleTheme">
        <div class="cursor" :class="{active : isDark}">
            <div class="icon">
                <i class="fa-solid" :class="isDark ? 'fa-moon' : 'fa-sun'"></i>
            </div>
        </div>
    </div>

</template>

<script setup>
    import { ref, onMounted, watch } from 'vue'

const isDark = ref(false)

// Charger la préférence au démarrage
onMounted(() => {
  const savedTheme = localStorage.getItem('theme')
  if (savedTheme === 'dark') {
    isDark.value = true
    document.body.classList.add('dark')
  }
})


watch(isDark, (value) => {
  if (value) {
    document.body.classList.add('dark')
    localStorage.setItem('theme', 'dark')
  } else {
    document.body.classList.remove('dark')
    localStorage.setItem('theme', 'light')
  }
})


const toggleTheme = () => {
  isDark.value = !isDark.value
}

</script>

<style scoped>
.container {
  position: relative;
  display: flex;
  align-items: center;
  background: #fff;
  width: 10rem;
  height: 5rem;
  border-radius: 10rem;
  padding: 0 0.5rem;
  cursor: pointer;
  box-shadow: 
    inset 0 8px 60px rgba(0,0,0,0.1),
    inset 0 8px 8px rgba(0,0,0,0.1),
    inset 0 -4px 4px rgba(0,0,0,0.1);
}

.cursor {
  position: absolute;
  background: #fff;
  width: 4.5rem;
  height: 4rem;
  border-radius: 50%;
  box-shadow: 0 8px 40px rgba(0,0,0,0.2);
  transition: transform 0.4s ease;
  display: flex;
  align-items: center;
  justify-content: center;
}

.cursor.active {
  transform: translateX(5.5rem);
}

.icon i {
  font-size: 1.5rem;
  color: #f39c12;
}

/* icône nuit */
.cursor.active i {
  color: #2c3e50;
}
i.animated{
    animation: spin 0.5s ease;
}
@keyframes spin {
    0%{
        transform: rotate(-360deg);
    }
}

</style>