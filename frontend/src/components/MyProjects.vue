<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import SectionTitle from './SectionTitle.vue'; // Asumsi Anda punya komponen
const projects = ref([]);
const API_URL = import.meta.env.PROD ? '/api/projects' :
'http://localhost:3000/api/projects';
onMounted(async () => {
try {
const response = await axios.get(API_URL);
projects.value = response.data;
} catch (error)
{
console.error('Gagal mengambil data proyek:', error);
}
});
</script>

<template>
<section id="proyek" class="py-20 bg-gradient-to-r from-[#fbe4e4] via-[#fdfaf6] to-[#c9e4ca]">
<div class="container mx-auto px-6">
<SectionTitle title="Proyek Unggulan" />
<div class="grid md:grid-cols-2 gap-12"><div v-for="project in projects" :key="project.title"
class="bg-[#fffaf0] rounded-lg shadow-lg overflow-hidden border border-[#e4cfc4]">
<img :src="project.image" alt="Gambar Proyek" class="w-full
h-56 object-cover">
<div class="p-6">
<h3 class="text-2xl font-bold text-[#854442] mb-2">{{
project.title }}</h3>
<p class="text-[#5c5b57] mb-4">{{ project.description }}</p>
<div class="mb-4">
<span v-for="t in project.tech" :key="t" class="inlineblock bg-[#fbd6d2] text-[#8e354a] text-sm font-semibold mr-2 mb-2 px-2.5
py-0.5 rounded-full">{{ t }}</span>
</div>
<a :href="project.link" target="_blank" rel="noopener
noreferrer" class="text-[#6a5d5d] font-semibold hover:text-[#8e354a] transition-colors duration-200">Lihat
Detail &rarr;</a>
</div>
</div>
</div>
</div>
</section>
</template>