<template>
  <section
    class="min-h-screen w-full flex items-center justify-center bg-transparent relative z-10"
  >
    <div class="max-w-5xl px-6 py-20 text-center">
      <p
        class="text-sm font-medium text-green-700/80 uppercase tracking-wide mb-4"
      >
        you really love this huh? 💚
      </p>
      <h1
        class="bg-gradient-to-r from-green-800 to-green-300 bg-clip-text text-transparent font-extrabold leading-tight md:leading-[0.9] text-[4rem] md:text-9xl uppercase"
      >
        zzyn
      </h1>
      <p class="mt-6 text-lg text-green-200 max-w-3xl mx-auto">
        This is the place where tired developers can just enjoy themselves into
        watching some animes/mangas
      </p>
    </div>
  </section>
</template>

<script setup lang="ts">
defineOptions({ name: 'AppHero' });
</script>

<style scoped>
.text-9xl {
  font-size: 9rem;
  line-height: 0.95;
}
</style>
