<template>
    <div class="p-6">
      <h1 class="font-bold text-4xl mb-6 text-orange-500">Ingredients</h1>
      <input type="text" v-model="keyword"   class="rounded border-2 bg-white border-gray-200 focus:ring-orange-500 focus:border-orange-500 mb-3 w-full"
        placeholder="Search For Ingredient">
  <div class="grid grid-cols-1 sm:grid-cols-2 gap-3  md:grid-cols-3 gap-3 ">
    <RouterLink :to="{name:'byIngredient' , params:{ingredient:ingredient.strIngredient},}" v-for="ingredient of computedIngredients" :key="ingredient.idIngredient" class="hover:scale-105 transition-all block bg-white rounded p-3 mb-3 shadow">
        <h3 class="text-2xl font-bold ">{{ ingredient.strIngredient }}</h3>
      </RouterLink>
  </div>
    </div>
  </template>
  
  <script setup>
  import { onMounted, ref, computed  } from 'vue';
  import axiosClient from '../axiosClient';
  const keyword = ref('');
  const ingredients = ref([])
  const computedIngredients = computed(() => {
  if (!computedIngredients) return ingredients;
  return ingredients.value.filter((i) =>
    i.strIngredient.toLowerCase().includes(keyword.value.toLowerCase())
  );
});
  onMounted(()=> 
      {
      axiosClient.get('list.php?i=list')
      .then(({data}) => {
        ingredients.value = data.meals
      })
      })
  </script>
  
  <style>
  
  </style>