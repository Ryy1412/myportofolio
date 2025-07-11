<script setup>
defineProps({ title: String });
</script>
<template>
  <div class="mb-12 text-center">
    <h2 class="text-4xl font-bold text-[#4c4637]">{{ title }}</h2>
    <div class="w-24 h-1 bg-[#a52a2a] mx-auto mt-4 rounded"></div>
  </div>
</template>