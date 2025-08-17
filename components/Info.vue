<template>
  <section
    id="info"
    class="w-full flex items-center justify-center relative z-10"
  >
    <div class="max-w-6xl w-full px-6 py-20">
      <div class="mx-auto max-w-4xl text-center">
        <p
          class="inline-flex items-center gap-3 px-4 py-2 rounded-full bg-black/30 text-green-200 text-sm font-semibold uppercase tracking-wide"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="w-4 h-4 text-green-300"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="1.5"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M12 20l9-7-9-7-9 7 9 7z"
            />
          </svg>
          Spotlight
        </p>
        <h2
          class="mt-6 text-[2.4rem] md:text-6xl font-extrabold bg-clip-text text-transparent bg-gradient-to-r from-green-300 to-green-800 leading-tight"
        >
          Anime & Manga Corner
        </h2>
        <p class="mt-4 text-lg text-green-200/90 max-w-2xl mx-auto">
          Discover scenes, characters and cozy recommendations — curated for
          tired devs who want to unwind with stunning art and gripping stories.
        </p>
      </div>

      <div class="mt-12 grid gap-6 grid-cols-1 md:grid-cols-3">
        <div
          class="flex flex-col items-start gap-4 p-6 rounded-2xl bg-gradient-to-b from-black/40 to-green-900/10 border border-green-800/30 shadow-lg backdrop-blur-sm transform hover:-translate-y-2 transition-all duration-400"
        >
          <div
            class="flex items-center justify-center w-14 h-14 rounded-lg bg-gradient-to-br from-green-700 to-green-900 text-white animate-float"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="w-7 h-7"
              viewBox="0 0 24 24"
              fill="currentColor"
            >
              <path
                d="M12 2C7 2 4 5 4 9c0 5 4 9 8 11 4-2 8-6 8-11 0-4-3-7-8-7z"
              />
            </svg>
          </div>
          <div>
            <h3 class="text-xl font-bold text-green-50">
              Chill Recommendations
            </h3>
            <p class="mt-2 text-green-200/90">
              Handpicked slice-of-life and comfort shows perfect for coding
              breaks.
            </p>
          </div>
        </div>

        <div
          class="flex flex-col items-start gap-4 p-6 rounded-2xl bg-gradient-to-b from-black/40 to-green-900/10 border border-green-800/30 shadow-lg backdrop-blur-sm transform hover:-translate-y-2 transition-all duration-400"
        >
          <div
            class="flex items-center justify-center w-14 h-14 rounded-lg bg-gradient-to-br from-purple-700 to-green-700 text-white animate-float animation-delay-200"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="w-7 h-7"
              viewBox="0 0 24 24"
              fill="currentColor"
            >
              <path d="M12 3l2 6h6l-5 4 2 6-5-4-5 4 2-6-5-4h6z" />
            </svg>
          </div>
          <div>
            <h3 class="text-xl font-bold text-green-50">Art & Panels</h3>
            <p class="mt-2 text-green-200/90">
              Stunning frames and character art to inspire your next UI or
              palette choice.
            </p>
          </div>
        </div>

        <div
          class="flex flex-col items-start gap-4 p-6 rounded-2xl bg-gradient-to-b from-black/40 to-green-900/10 border border-green-800/30 shadow-lg backdrop-blur-sm transform hover:-translate-y-2 transition-all duration-400"
        >
          <div
            class="flex items-center justify-center w-14 h-14 rounded-lg bg-gradient-to-br from-green-500 to-green-800 text-white animate-float animation-delay-400"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="w-7 h-7"
              viewBox="0 0 24 24"
              fill="currentColor"
            >
              <path d="M4 5h16v2H4zM4 11h10v2H4zM4 17h16v2H4z" />
            </svg>
          </div>
          <div>
            <h3 class="text-xl font-bold text-green-50">Quick Reads</h3>
            <p class="mt-2 text-green-200/90">
              Short manga picks and one-shot suggestions to finish between
              tasks.
            </p>
          </div>
        </div>
      </div>

      <div class="mt-10 flex items-center justify-center">
        <a
          href="#recommendations"
          class="inline-flex items-center gap-3 px-6 py-3 rounded-full bg-gradient-to-r from-green-700 to-green-900 text-white font-semibold shadow-lg hover:scale-105 transition transform duration-200"
        >
          Explore Now
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="w-4 h-4"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="2"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              d="M17 8l4 4m0 0l-4 4m4-4H3"
            />
          </svg>
        </a>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
defineOptions({ name: 'AppInfo' });
</script>

<style scoped>
@keyframes float {
  0% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-6px);
  }
  100% {
    transform: translateY(0px);
  }
}
.animate-float {
  animation: float 3s ease-in-out infinite;
}
.animation-delay-200 {
  animation-delay: 0.2s;
}
.animation-delay-400 {
  animation-delay: 0.4s;
}
</style>
