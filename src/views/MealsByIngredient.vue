<template>
<div>
  <div class="grid grid-cols-1 md:grid-cols-4 gap-4 p-8">
        <MealItem v-for="meal of meals" :key="meal.idmeals" :meal="meal" />
  </div>
  <div v-if="!meals.length" class="flex justify-center text-gray-600 p-8">
    There are no meals
  </div>
</div>
</template>

<script setup>
import { computed } from '@vue/reactivity';
import { onMounted, watch } from 'vue';
import {useRoute } from 'vue-router';
import store from '../store';
import MealItem from '../components/MealItem.vue';
const route = useRoute()
const meals = computed(() => store.state.mealsByIngredient)
onMounted(()=>
{
    store.dispatch('searchMealsByIngredient' , route.params.ingredient)
})
</script>

<style>

</style>