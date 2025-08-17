<template>
  <div class="min-h-screen w-full bg-black" aria-hidden="true">
    <div
      class="absolute inset-0 z-0"
      style="
        background: radial-gradient(
            ellipse 90% 70% at 50% 0%,
            rgba(16, 185, 129, 0.65),
            transparent 65%
          ),
          #000000;
      "
    />
    <div class="z-10">
      <Hero />
    </div>
    <Info />
    <Recommendations />
    <BookADemo />
    <ContactUs />
  </div>
</template>

<script setup lang="ts">
import Hero from '~/components/Hero.vue';
import Info from '~/components/Info.vue';
import Recommendations from '~/components/Recommendations.vue';
import BookADemo from './components/BookADemo.vue';
import ContactUs from './components/ContactUs.vue';
</script>
