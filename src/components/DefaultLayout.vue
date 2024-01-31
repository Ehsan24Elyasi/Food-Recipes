<template>
<div class="h-full bg-gray-100 text-lg font-semibold ">
    <Navbar />

    <main >
    <router-view />
    </main>
</div>

</template>

<script setup>
import Navbar from '../components/Navbar.vue';
</script>

<style>

</style>