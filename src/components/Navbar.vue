<template>
  
  <header class="bg-white shadow h-16 flex justify-between items-stretch">

<router-link :to="{name: 'home'}" class="inline-flex items-center px-5">
  Home
</router-link>

<div class="flex gap-1">
  <router-link :to="{name: 'byName'}" class=" items-center px-2 inline-flex h-full hover:bg-purple-100 transition-colors">
    Meals by Name   
</router-link>
<router-link :to="{name: 'byLetter'}" class="items-center px-2 inline-flex h-full hover:bg-purple-100 transition-colors">
  Meals by Letter   
</router-link>
<router-link :to="{name: 'byIngredient'}" class="items-center px-2 inline-flex h-full hover:bg-purple-100 transition-colors">
  Meals by Ingredients
</router-link>

</div>

</header>


</template>

<script setup>

</script>

<style>

</style>