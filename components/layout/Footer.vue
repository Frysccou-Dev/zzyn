<template>
  <footer class="w-full">
    <div
      class="max-w-7xl mx-auto px-6 py-8 flex flex-wrap items-center justify-between gap-6"
    >
      <div class="flex flex-col gap-1">
        <div
          class="text-2xl font-extrabold tracking-tight bg-clip-text text-transparent bg-gradient-to-r from-green-300 to-green-800 brand-glow"
        >
          zzyn
        </div>
        <div class="text-sm text-green-200/80">
          Curated anime & manga picks for devs
        </div>
      </div>

      <nav class="flex items-center gap-3 flex-1 justify-center">
        <a
          href="#info"
          class="text-sm px-3 py-1 rounded-full bg-black/10 text-green-200 hover:bg-black/20 hover:text-white transition transform hover:-translate-y-0.5"
        >
          About
        </a>
        <a
          href="#recommendations"
          class="text-sm px-3 py-1 rounded-full bg-black/10 text-green-200 hover:bg-black/20 hover:text-white transition transform hover:-translate-y-0.5"
        >
          Recommendations
        </a>
        <a
          href="#demo-form"
          class="text-sm px-3 py-1 rounded-full bg-black/10 text-green-200 hover:bg-black/20 hover:text-white transition transform hover:-translate-y-0.5"
        >
          Request demo
        </a>
        <a
          href="#contact"
          class="text-sm px-3 py-1 rounded-full bg-black/10 text-green-200 hover:bg-black/20 hover:text-white transition transform hover:-translate-y-0.5"
        >
          Contact
        </a>
      </nav>

      <div class="flex flex-col items-end gap-2">
        <div class="flex items-center gap-3">
          <a
            href="https://www.linkedin.com/in/espindola-francisco/"
            target="_blank"
            rel="noopener"
            aria-label="LinkedIn"
            class="w-10 h-10 flex items-center justify-center rounded-lg bg-black/10 text-green-300 hover:bg-black/20 hover:text-green-400 transition transform hover:-translate-y-1"
          >
            <Linkedin class="w-5 h-5" />
          </a>

          <a
            href="https://music.youtube.com/playlist?list=PLr8nCm0aobtRA0SAeeK4Fa9tbWf-r-ton"
            target="_blank"
            rel="noopener"
            aria-label="YouTube Music"
            class="w-10 h-10 flex items-center justify-center rounded-lg bg-black/10 text-green-300 hover:bg-black/20 hover:text-green-400 transition transform hover:-translate-y-1"
          >
            <Youtube class="w-5 h-5" />
          </a>

          <a
            href="https://github.com/esspindola"
            target="_blank"
            rel="noopener"
            aria-label="GitHub"
            class="w-10 h-10 flex items-center justify-center rounded-lg bg-black/10 text-green-300 hover:bg-black/20 hover:text-green-400 transition transform hover:-translate-y-1"
          >
            <Github class="w-5 h-5" />
          </a>

          <a
            href="https://www.instagram.com/Frysccou/"
            target="_blank"
            rel="noopener"
            aria-label="Instagram"
            class="w-10 h-10 flex items-center justify-center rounded-lg bg-black/10 text-green-300 hover:bg-black/20 hover:text-green-400 transition transform hover:-translate-y-1"
          >
            <Instagram class="w-5 h-5" />
          </a>
        </div>

        <div class="text-right text-sm text-green-200/75">
          <div class="font-semibold text-green-100">
            © <span class="now">2025</span> zzyn
          </div>
          <div class="text-green-200/60">
            Made for fans · All rights reserved
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup lang="ts">
import { Linkedin, Youtube, Github, Instagram } from 'lucide-vue-next';
</script>

<style scoped>
.brand-glow {
  animation: brandGlow 6s linear infinite;
}
@keyframes brandGlow {
  0% {
    filter: drop-shadow(0 0 0 rgba(22, 163, 74, 0));
  }
  50% {
    filter: drop-shadow(0 10px 30px rgba(22, 163, 74, 0.12));
  }
  100% {
    filter: drop-shadow(0 0 0 rgba(22, 163, 74, 0));
  }
}
@media (prefers-reduced-motion: reduce) {
  .brand-glow {
    animation: none;
  }
}
</style>
