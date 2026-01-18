<template>
    <div class="container">
        <div class="cursor">
            <div class="icon">
                <i class="fa-solid"></i>
            </div>
        </div>
    </div>

</template>

<script setup>

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
    box-shadow: 
    inset 0 8px 60px rgba(0,0,0,0.1),
    inset 0 8px 8px rgba(0,0,0,0.1),
    inset 0 -4px 4px rgba(0,0,0,0.1);

}
.cursor {
    position: absolute;
    background:#fff; 
    width: 4.5rem;
    height: 4rem;
    border-radius: 50%;
    box-shadow: 0 8px 40px rgba(0,0,0,0.2);
    transition: transform 0.5s ease;
}

</style>