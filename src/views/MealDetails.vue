<template>
  <div class="max-w-[800px]  mx-auto">
    <h1 class="text-4xl font-bold mb-5 text-orange-500">{{ meal.strMeal }}</h1>
    <img :src="meal.strMealThumb" :alt="meal.strMeal">
    <div class="mt-5 mb-8 grid grid-cols-1 md:grid-cols-3">
        <div>
           <strong class="font-bold"> category:</strong>{{ meal.strCategory }}
        </div>
        <div>
            <strong class="font-bold">Area: </strong>{{ meal.strArea }}
        </div>
        <div>
            <strong class="font-bold">Tags: </strong>{{ meal.strTags }}
        </div>
    </div>

    <div class="mb-5 font-normal text-lg">
      {{ meal.strInstructions }}
    </div>

    <div  class="grid grid-cols-1 sm:grid-cols-2">
      <div>
        <h2 class="text-2xl font-semibold mb-3">Ingredients</h2>
    <ul>
      <template  v-for="(el , ind) of new Array(30)" >
        <li class="font-normal text-lg" v-if="meal[`strIngredient${ind + 1}`]" :key="ind">
          {{ ind + 1 }}. {{ meal[`strIngredient${ind + 1}`] }}
        </li>
      </template>
    </ul>
      </div>
      <div>
        <h2 class="text-2xl font-semibold mb-3"> Measures</h2>
        <ul>
      <template v-for="(el , ind) of new Array(30)" >
        <li class="font-normal text-lg" v-if="meal[`strMeasure${ind + 1}`]" :key="ind">
          {{ ind + 1 }}.  {{ meal[`strMeasure${ind + 1}`] }}
        </li>
      </template>
    </ul>
   </div>
   <div class="mt-10 mb-5">
    <YouTubeButton :href="meal.strYoutube" />
    <a class="px-3 py-2 text-indigo-700" :href="meal.strSource" target="_blank"> View Original Source </a>
   </div>
    </div>
  </div>
</template>

<script setup>
import { ref , onMounted } from 'vue';
import { useRoute  } from 'vue-router';
import axiosClient from '../axiosClient';
import YouTubeButton from '../components/YouTubeButton.vue';
const route = useRoute();
const meal = ref({});

onMounted(() => {
  axiosClient.get(`lookup.php?i=${route.params.id}`) 
    .then(({ data }) => {
      meal.value = data.meals[0] || {}
    })
})
</script>

<style>

</style>