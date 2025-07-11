<script setup>
import SectionTitle from './SectionTitle.vue';

function openGmail() {
  const email = 'rayyishammam@gmail.com';
  const subject = 'Kontak dari Website';
  const body = 'Halo, saya tertarik untuk menghubungi anda...';

  const gmailUrl = `https://mail.google.com/mail/?view=cm&fs=1&to=${email}&su=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;
  window.open(gmailUrl, '_blank');
}
</script>

<template>
<footer id="kontak" class="py-20 bg-gradient-to-b from-[#fcefe8] to-[#4a3f3f]">
<div class="container mx-auto px-6 text-center">
<SectionTitle title="Hubungi Saya" />
<p class="text-xl text-[#e5dad4] mb-8">Jangan ragu untuk terhubung atau bertanya.</p>
<button @click="openGmail"
        class="bg-[#8e354a] text-white font-bold py-3 px-6 rounded-lg hover:bg-[#a75d67] transition-colors duration-300 inline-block mb-12">
        Kirim Email
</button>
<div class="flex justify-center space-x-6 mb-8">

<a href="https://github.com/Ryy1412" target="_blank" class="text-[#eacfc3] hover:text-[#fbd6d2] transition-colors duration-300">GitHub</a>

<a href="https://www.linkedin.com/in/rayyis-hammam-02399a373/" target="_blank" class="text-[#eacfc3] hover:text-[#fbd6d2] transition-colors duration-300">LinkedIn</a>

</div>
<p class="text-[#d0bfb7]">&copy; {{ new Date().getFullYear() }} Rayyis Hammam Mukhayyar. Dibuat dengan senyum dan semangat ^w^
</p>
</div>
</footer>
</template>