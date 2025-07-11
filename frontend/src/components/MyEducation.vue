<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import SectionTitle from './SectionTitle.vue'; // Asumsi Anda punya komponen
const educationHistory = ref([]);
const API_URL = import.meta.env.PROD ? '/api/education' :
'http://localhost:3000/api/education';
onMounted(async () => {
try {
const response = await axios.get(API_URL);
educationHistory.value = response.data;
} catch (error) {
console.error('Gagal mengambil data pendidikan:', error);
}
});
</script>
<template>
<section id="pendidikan" class="py-20 bg-gradient-to-r from-[#a8dadc] via-[#f1faee] to-[#f4a261]">
<div class="container mx-auto px-6">
<SectionTitle title="Riwayat Pendidikan" />
<div class="relative">
<div class="absolute h-full border-r-2 border-[#e9c46a]"
style="left: 50%;"></div>
<div v-for="(edu, index) in educationHistory" :key="edu.id"
class="mb-8 flex justify-between items-center w-full">
<div v-if="index % 2 === 0" class="w-full flex">
<div class="w-1/2 pr-8 text-right"><p class="font-semibold
text-[#3d5a80]">{{ edu.period }}</p><h3 class="text-2xl font-bold text-[#264653]">{{ edu.institution }}</h3><p class="text-[#e76f51]">{{
edu.major }}</p></div>
<div class="w-1/2 flex justify-start"><div class="w-4 h-4
bg-[#f4a261] rounded-full z-10"></div></div>
</div>
<div v-else class="w-full flex">
<div class="w-1/2 flex justify-end"><div class="w-4 h-4 bg-[#f4a261] rounded-full z-10"></div></div>
<div class="w-1/2 pl-8 text-left"><p class="font-semibold
text-[#3d5a80]">{{ edu.period }}</p><h3 class="text-2xl font-bold text-[#264653]">{{ edu.institution }}</h3><p class="text-[#5c5b57]">{{
edu.major }}</p></div>
</div>
</div>
</div>
</div>
</section>
</template>