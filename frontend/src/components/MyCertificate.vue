<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import SectionTitle from './SectionTitle.vue'; // Asumsi Anda punya komponen
const certificate = ref([]);
const API_URL = import.meta.env.PROD ? '/api/certificate' :
'http://localhost:3000/api/certificate';
onMounted(async () => {
try {
const response = await axios.get(API_URL);
certificate.value = response.data;
} catch (error)
{
console.error('Gagal mengambil data proyek:', error);
}
});
</script>

<template>
  <section id="certificate" class="py-20 bg-gradient-to-r from-[#fdfaf6] via-[#dcedc1] to-[#c9e4ca]">
    <div class="container mx-auto px-6">
      <SectionTitle title="Sertifikat" />
      <div class="grid md:grid-cols-2 gap-12">
        <div
          v-for="item in certificate"
          :key="item.title"
          class="bg-[#fffaf0] rounded-lg shadow-lg overflow-hidden border border-[#e4cfc4]"
        >
          <img :src="item.image" alt="Gambar certificate" class="w-full h-56 object-cover" />
          <div class="p-6">
            <h3 class="text-2xl font-bold text-[#6a3e3e] mb-2">{{ item.title }}</h3>
            <p class="text-[#6f5f5f] mb-4">{{ item.description }}</p>
            <div class="mb-4">
              <span
                v-for="tech in item.tech"
                :key="tech"
                class="inline-block bg-[#fce1dd] text-[#944040] text-sm font-semibold mr-2 mb-2 px-2.5 py-0.5 rounded-full"
              >
                {{ tech }}
              </span>
            </div>
            <a
              :href="item.link"
              target="_blank"
              rel="noopener noreferrer"
              class="text-[#7a6b6b] font-semibold hover:text-[#8e354a] transition-colors duration-200"
            >
              Lihat Detail &rarr;
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
