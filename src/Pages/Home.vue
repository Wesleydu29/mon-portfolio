<template>
    <Banner content="Mes projets"/>
    <Projets/>
    <Banner content="À propos de moi"/>
    <section id="about">
        <Introducing/>
    </section>
    <Softskills/>
    <Banner content="Contactez moi"/>
    <section id="contact">
        <Form/>
    </section>



</template>

<script setup>

import Projets from '@/components/Projets.vue';
import Banner from '@/components/Banner.vue';
import Introducing from '@/components/Introducing.vue';
import Softskills from '@/components/Softskills.vue';
import Form from '@/components/Form.vue';

</script>

<style scoped>
html {
    scroll-behavior: smooth;
}
</style>
