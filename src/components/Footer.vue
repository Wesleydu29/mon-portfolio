<template>
    <div class="footer">
        <p> {{date}} Goarant Wesley. Full-Stack Developer</p>
    </div>

</template>
<script setup>

import { ref } from 'vue';

const date = ref(new Date().getFullYear())

</script>

<style scoped>
.footer {
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 1.2rem;
    
}
</style>