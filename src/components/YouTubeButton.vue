<template>
         <a class="px-3 py-2  border-2 border-red-600 bg-red-600 text-white rounded-lg transition-colors
         hover:bg-red-700" :href="href" target="_blank">YouTube</a>
</template>

<script setup>

const props = defineProps(
    {
        href: String
    })
</script>
<style>

</style>