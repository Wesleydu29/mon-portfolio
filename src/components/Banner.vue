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
    background-image: url(/public/images/appartement-paris-v.png);
    background-position: center;
    background-size: cover;
    width: 100%;
    height: 100px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 2em;
}
.banner h2 {
    font-size: 3rem;
}

</style>