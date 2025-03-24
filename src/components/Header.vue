<template>
    <header>
        <h1>Bienvenu sur mon portfolio</h1>
        <nav>
            <ul>
                <li><a href="#" class="hover:underline">Accueil</a></li>
                <li><a href="#" class="hover:underline">Projets</a></li>
                <li><a href="#" class="hover:underline">Contact</a></li>
            </ul>
        </nav>
    </header>

</template>


<script setup> 

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