<template>
   <div class="flex gap-6 justify-center mt-8">
        <router-link :to="{name: 'byLetter' , params:{letter}}" v-for="letter of letters" :key="letter" >
        {{ letter }}
        </router-link>
    </div> 
</template>

<script setup>
import {computed , onMounted , ref} from 'vue';
import store from '../store';
import axiosClient from '../axiosClient.js';
const ingredients = ref([])
const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split("")
onMounted(async()=>
{
    const response = await axiosClient.get('/list.php?i=list')
    ingredients.value = response.data
})
const meals = computed(() => store.state.meals)
</script>

<style>

</style>