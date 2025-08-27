<template>
    <div class="container">
        <div class="introducing">
            <p>Je m'appelle Wesley, j'ai 25ans et depuis quelques années maintenant je me suis découvert une nouvelle passion, le développement web, plus précisément le développement front-end, avec des bases en back-end. 
                Je suis actuellement à la recherche d'une alternance pour la rentrée 2025 à compter de septembre, pour un bachelor IT developpeur full stack. 
                Alors si vous passez par là et que mon profil vous intéresse, n'hésitez pas à me contacter pour discuter davantage.
            </p>
            <img src="/images/profil.jpg" alt="portrait Wesley Goarant">
        </div>
        
    </div>

</template>

<script setup>

</script>

<style scoped>
.container {
    margin-top: 2rem;
    background-color: bisque;
    padding: 20px;
}
.introducing {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 100px;
}
.introducing p {
    width: 30%;
    font-size: 1.2rem;
}
.introducing img {
    width: 300px;
    height: auto;
}
.left,
.right {
    flex-basis: 50%;
}

</style>