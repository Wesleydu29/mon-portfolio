<template>
    <div class="container">
        <div class="form-group">
            <h3>Envoyez moi un mail et je vous repondrez au plus vite</h3>
            <label for="nom">Nom</label>
            <input type="text" id="nom">
            <label for="prénom">Prénom</label>
            <input type="text"  id="prénom">
            <textarea name="" id="" placeholder="écrivez votre message"></textarea>
        </div>

    </div>

</template>

<script setup>
</script>

<style scoped>
* {
    box-sizing: border-box;
}
.container {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center ;
}
.form-group {
    width: 550px;
    padding: 5px;
}
label {
    align-self: flex-start;
}
input {
    height: 2rem;
    margin-bottom: 1rem;
}
input, textarea {
    width: 100%;
}
textarea {
    height: 200px;
}
</style>