<template>
<div class="p-8 pb-0">
    <h1 class="text-4xl font-bold mb-2 text-orange-500">Search Meals by Name</h1>
    <div class="flex justify-center p-4">
        <input type="text" v-model="keyword"  class="rounded border-2 bg-white border-gray-200 focus:ring-orange-500 focus:border-orange-500 w-full" 
        placeholder="Search For Meals"
        @change="searchMeals">
    </div>
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
const meals = computed(()=>store.state.searchedMeals);
function searchMeals()
    {
        if(keyword.value)
        store.dispatch("searchMeals", keyword.value);   
        else
        store.commit("setSearchedMeals", []);   
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