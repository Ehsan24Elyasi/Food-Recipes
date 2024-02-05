<template>
      <div  class="bg-white shadow rounded-xl hover:scale-105 transition-all">

           <router-link :to="{name:'mealDetails' , params:{id:meal.idMeal}}">
            <img class="w-full h-48 object-cover rounded-t-xl" :src="meal.strMealThumb" :alt="strMeal">
           </router-link>

            <h3 class="p-3 font-bold">{{ meal.strMeal }}</h3>
            <p class="mb-4 ml-3 font-normal text-base">
            {{ Instructions }}
            </p>
            
            <div class="p-3">
            <YouTubeButton :href="meal.strYoutube" />
            </div>
        </div>
</template>

<script setup>
import YouTubeButton from '../components/YouTubeButton.vue'
const { meal } = defineProps({
    meal:{
        required: true,
        href: Object
    }
})
let Instructions;
if (meal.strInstructions)
{
    Instructions = meal.strInstructions.substring(0,120)+" ..."
}
</script>

<style>

</style>