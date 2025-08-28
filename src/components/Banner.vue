<template>

    <div class="banner">
        <div class="about">
            <h2>{{ content }}</h2>

        </div>

    </div>

</template>

<script setup>

defineProps({
    content: {
        type: String,
        required: true
    }
})

</script>

<style scoped>
.banner {
    background-color: rgba(119, 150, 203, 0.5) ;
    width: 100%;
    height: 100px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 2em;
}
.banner h2 {
    font-size: 3rem;
    color: #000;
    font-family: 'poppins', sans-serif;
}

</style>