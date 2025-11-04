<template>
    <header>
        <h1>Bienvenu sur mon portfolio</h1>
        <nav>
            <ul>
                <li v-for="(link, index) in links" :key="index">
                    <a :href="link.href">{{ link.name }}</a>
                </li>
            </ul>
        </nav>
    </header>

</template>


<script setup> 

import { ref } from 'vue';

const links = ref([
    { name: "À propos", href: "#about" },
    { name: "Contact", href: "#contact" }
]);

</script>


<style scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px solid #000000;
}
a {
    color: #000000;
    text-decoration: none;
    font-size: 1.3rem;
}
ul {
    display: flex;
    gap: 10px;
    list-style: none;
}
</style>