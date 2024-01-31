<template>
<div class="p-8 pb-0">
    <div class="flex justify-center p-8">
        <input type="text" v-model="keyword" class=" m-4 rounded border-2 border-gray-200 w-full" 
        placeholder="Search For Meals"
        @change="searchMeals">
    </div>
    <div class="grid grid-cols-1 md:grid-cols-4 gap-4 p-8">
        <div v-for="meal of meals" :key="meal.idmeals" class="bg-white shadow rounded-xl">
           <router-link :to="{name:'mealDetails' , params:{id:meal.idMeal}}">
            <img class="w-full h-48 object-cover rounded-t-xl" :src="meal.strMealThumb" :alt="strMeal">
           </router-link>
            <h3 class="p-3 font-bold">{{ meal.strMeal }}</h3>
            <div class="p-3">
            <YouTubeButton :href="meal.strYoutube" />
            </div>
        </div>
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
const keyword = ref('');
const route = useRoute();
const meals = computed(()=>store.state.searchedMeals);
function searchMeals()
    {
        store.dispatch("searchMeals", keyword.value);   
    }
    onMounted(()=>
    {
        keyword.value = route.params.name;
        if(keyword.value)
        {
            searchMeals()
        }
    })
</script>

<style>

</style>