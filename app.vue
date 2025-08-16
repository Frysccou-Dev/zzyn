<template>
  <div class="min-h-screen w-full bg-black" aria-hidden="true">
    <div
      class="absolute inset-0 z-0"
      style="
        background: radial-gradient(
            ellipse 80% 60% at 50% 0%,
            rgba(16, 185, 129, 0.25),
            transparent 70%
          ),
          #000000;
      "
    />
    <div class="z-10">
      <Hero />
    </div>
    <Info />
    <Recommendations />
  </div>
</template>

<script setup lang="ts">
import Hero from '~/components/Hero.vue';
import Info from '~/components/Info.vue';
import Recommendations from '~/components/Recommendations.vue';
</script>
