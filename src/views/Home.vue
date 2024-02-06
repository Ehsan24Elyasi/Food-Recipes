<template>
  <div class="p-8 pb-0">
      <h1 class="text-4xl font-bold mb-2 text-orange-500"> Random Meals </h1>
      <div   class="grid grid-cols-1 md:grid-cols-4 gap-4 p-8">
      <MealItem v-for="meal of meals" :key="meal.idmeals" :meal="meal" />
      </div>
      <div v-if="!meals.length" class="flex justify-center text-gray-600 font-normal">
      There are no meals
    </div>
  </div>
  </template>
  
  <script setup>
  import { onMounted, ref  } from 'vue';
  import { computed  } from '@vue/reactivity';
  import { useRoute  } from 'vue-router';
  import axiosClient from '../axiosClient';
  import store from '../store';
  import YouTubeButton from '../components/YouTubeButton.vue';
  import MealItem from '../components/MealItem.vue';
  const keyword = ref('');
  const route = useRoute();

  const meals = ref([]);

  onMounted(async () => {
    for (let i = 0; i < 10; i++) {
      axiosClient
        .get(`random.php`)
        .then(({ data }) => meals.value.push(data.meals[0]));
    }
  }); 
  </script>
  
  <style>
  
  </style>