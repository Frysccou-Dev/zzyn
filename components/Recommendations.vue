<template>
  <section
    class="w-full min-h-screen flex items-center justify-center bg-transparent relative z-10"
  >
    <div class="max-w-6xl w-full px-6 py-20">
      <div class="mx-auto max-w-4xl text-center">
        <p
          class="inline-block px-3 py-1 text-xs font-semibold uppercase tracking-wider rounded-full bg-green-900/40 text-green-200"
        >
          Animes
        </p>
        <h2
          class="mt-6 text-[2.4rem] md:text-6xl font-extrabold bg-clip-text text-transparent bg-gradient-to-r from-green-300 to-green-800 leading-tight"
        >
          Animes WE recommend
        </h2>
        <p class="mt-4 text-lg text-green-200/90 max-w-2xl mx-auto">
          Handpicked anime picks for relaxing breaks, full of heart, style and
          unforgettable moments.
        </p>
      </div>

      <div class="mt-12">
        <div class="flex items-center justify-center gap-4">
          <button
            class="p-2 rounded-full bg-black/30 text-green-200 hover:bg-black/40 transition"
            :aria-label="'Previous'"
            @click="prev"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="w-5 h-5"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              stroke-width="2"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M15 19l-7-7 7-7"
              />
            </svg>
          </button>

          <div
            role="tablist"
            class="flex flex-wrap justify-center gap-3 max-w-full"
          >
            <button
              v-for="(r, i) in recommendations"
              :key="r.id"
              :aria-selected="i === activeIndex"
              :class="[
                'px-4 py-2 rounded-full font-medium transition-all focus:outline-none',
                i === activeIndex
                  ? 'bg-gradient-to-r from-green-600 to-green-900 text-white shadow-lg scale-105'
                  : 'bg-black/30 text-green-200 hover:scale-105',
              ]"
              @click="select(i)"
              @keydown.enter.prevent="select(i)"
            >
              <span
                class="md:hidden max-w-[160px] overflow-hidden truncate block"
                >{{ r.short }}</span
              >
              <span
                class="hidden md:inline max-w-[300px] overflow-hidden truncate block"
                >{{ r.title }}</span
              >
            </button>
          </div>

          <button
            class="p-2 rounded-full bg-black/30 text-green-200 hover:bg-black/40 transition"
            :aria-label="'Next'"
            @click="next"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="w-5 h-5"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              stroke-width="2"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M9 5l7 7-7 7"
              />
            </svg>
          </button>
        </div>

        <div class="mt-8">
          <transition name="fancy-card" mode="out-in">
            <div
              :key="active?.id"
              class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center"
            >
              <div class="rounded-2xl shadow-2xl">
                <div class="frame" :style="frameStyle">
                  <div class="portrait w-full">
                    <img
                      :src="active?.image"
                      :alt="active?.title"
                      class="w-full h-full object-cover transform hover:scale-105 transition-transform duration-500"
                    />
                  </div>
                </div>
              </div>

              <div>
                <h3
                  class="text-2xl md:text-4xl font-extrabold text-green-50 leading-tight"
                >
                  {{ active?.title }}
                </h3>
                <p class="mt-4 text-lg text-green-200/90">
                  {{ active?.description }}
                </p>

                <div class="mt-6">
                  <div
                    class="inline-flex items-center gap-3 px-4 py-2 rounded-full bg-gradient-to-r from-black/40 to-green-900/20 border border-green-800/30 text-green-100"
                  >
                    <span class="font-semibold">Why we recommend</span>
                  </div>
                  <p class="mt-3 text-green-200/80">
                    {{ active?.reason }}
                  </p>
                </div>

                <div class="mt-8 flex gap-3">
                  <a
                    :href="active?.link"
                    class="inline-flex items-center gap-2 px-5 py-3 rounded-full bg-gradient-to-r from-green-700 to-green-900 text-white font-semibold shadow-lg hover:scale-105 transition transform duration-200"
                  >
                    Learn more
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
            </div>
          </transition>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue';

const recommendations = [
  {
    id: 'a1',
    tag: 'Romance',
    short: 'Secret Crush',
    title: 'Alya Sometimes Hides Her Feelings in Russian',
    image: '/alya-banner.jpg',
    description:
      'A charming rom-com where a shy boy understands the Russian mumbles of his seemingly cold classmate, who is unaware that he can hear her true, heartfelt feelings.',
    reason:
      'A fresh and witty take on the classic rom-com with great character dynamics and funny, heartwarming misunderstandings that keep you hooked.',
    link: 'https://anilist.co/anime/181641/Tokidoki-Bosotto-Russiago-de-Dereru-Tonari-no-Alyasan-Season-2/',
  },
  {
    id: 'a2',
    tag: 'Slice of Life',
    short: 'Cosplay Fun',
    title: 'My Dress-Up Darling',
    image: '/dressup-banner.jpg',
    description:
      'A heartwarming story about a lonely boy who loves traditional dolls and a popular girl with a secret passion for cosplay, as they collaborate and grow closer.',
    reason:
      'Visually stunning and incredibly wholesome, this series beautifully explores passion and self-discovery with a feel-good romance that will lift your spirits.',
    link: 'https://anilist.co/anime/154768/My-DressUp-Darling-Season-2/',
  },
  {
    id: 'a3',
    tag: 'Fantasy',
    short: 'Beyond Time',
    title: "Frieren: Beyond Journey's End",
    image: '/frieren-banner.jpg',
    description:
      'An epic fantasy following the long-lived elf mage Frieren as she travels after the defeat of the Demon King, reflecting on her relationships and the passage of time.',
    reason:
      'A unique and profound fantasy series with a gentle pace and breathtaking animation that tackles deep themes of friendship, legacy, and the nature of life itself.',
    link: 'https://anilist.co/anime/154587/Frieren-Beyond-Journeys-End/',
  },
  {
    id: 'a4',
    tag: 'Drama',
    short: 'Emotional Read',
    title: "Takopi's Original Sin",
    image: '/takopi-banner.jpg',
    description:
      'A dark and powerful manga about an innocent alien who tries to bring happiness to an abused and lonely girl, leading to a tragic and profound journey.',
    reason:
      'A must-read for its poignant and mature storytelling. It explores heavy themes with a unique art style, creating a deeply moving and unforgettable narrative.',
    link: '#',
  },
  {
    id: 'a5',
    tag: 'Thriller',
    short: 'Idol Mystery',
    title: 'Oshi no Ko',
    image: '/oshinoko-banner.png',
    description:
      'A gripping mystery-drama about a doctor reincarnated as the son of his favorite idol, as he navigates the dark secrets and intense pressures of the entertainment industry.',
    reason:
      'An explosive and original story that combines a shocking mystery with a realistic look at the idol world. It’s a fast-paced thriller with intelligent writing and unexpected twists.',
    link: 'https://anilist.co/anime/185407/Takopis-Original-Sin/',
  },
];

const activeIndex = ref(0);
const active = computed(() => recommendations[activeIndex.value]);

const gradients = [
  ['#A7DFF0', '#EDBAD1', '#FAE4EF', '#F8F810'],
  ['#7B6146', '#44372F', '#93B8B8', '#944946'],
  ['#22c55e', '#16a34a', '#4ade80', '#10b981', '#065f46'],
  ['#1A77A1', '#F7506B', '#F7D384', '#ADD8CC'],
  ['#C322B9', '#FDF2FE', '#D8D4FC', '#FBD2EB'],
];

const frameStyle = computed(() => {
  const cols = gradients[activeIndex.value] ??
    gradients[2] ?? ['#22c55e', '#16a34a', '#4ade80', '#10b981', '#065f46'];
  return {
    '--frame-gradient': `linear-gradient(90deg, ${cols.join(', ')})`,
  };
});

function select(i: number) {
  activeIndex.value = i;
}

function prev() {
  activeIndex.value =
    (activeIndex.value - 1 + recommendations.length) % recommendations.length;
}

function next() {
  activeIndex.value = (activeIndex.value + 1) % recommendations.length;
}

defineOptions({ name: 'AnimeRecomendations' });
</script>

<style scoped>
.fancy-card-enter-active {
  animation: fancy-in 640ms cubic-bezier(0.22, 1, 0.36, 1) both;
}
.fancy-card-leave-active {
  animation: fancy-out 420ms cubic-bezier(0.55, 0.06, 0.68, 0.19) both;
}
@keyframes fancy-in {
  0% {
    opacity: 0;
    transform: perspective(900px) translateY(20px) scale(0.98) rotateX(12deg);
    filter: blur(8px);
  }
  60% {
    opacity: 1;
    transform: perspective(900px) translateY(-8px) scale(1.03) rotateX(-4deg);
    filter: blur(2px);
  }
  100% {
    opacity: 1;
    transform: perspective(900px) translateY(0) scale(1) rotateX(0);
    filter: none;
  }
}
@keyframes fancy-out {
  0% {
    opacity: 1;
    transform: perspective(900px) translateY(0) scale(1) rotateX(0);
    filter: none;
  }
  100% {
    opacity: 0;
    transform: perspective(900px) translateY(-12px) scale(0.98) rotateX(8deg);
    filter: blur(6px);
  }
}
.fancy-card-enter-active .portrait img {
  animation: image-pop 760ms cubic-bezier(0.22, 1, 0.36, 1) both;
  animation-delay: 80ms;
}
@keyframes image-pop {
  0% {
    opacity: 0;
    transform: scale(1.06) rotate(-2deg);
    filter: blur(6px);
  }
  60% {
    opacity: 1;
    transform: scale(1.01) rotate(0.5deg);
    filter: blur(1px);
  }
  100% {
    opacity: 1;
    transform: scale(1) rotate(0deg);
    filter: none;
  }
}
.fade-slide-enter-active,
.fade-slide-leave-active {
  animation: fade-slide 420ms cubic-bezier(0.2, 0.9, 0.2, 1);
}
@keyframes fade-slide {
  0% {
    opacity: 0;
    transform: translateY(8px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}
.portrait {
  aspect-ratio: 2 / 3;
  overflow: hidden;
  border-radius: 1rem;
  position: relative;
  z-index: 2;
}
.frame {
  position: relative;
  display: block;
}
.frame::before {
  content: '';
  position: absolute;
  inset: -6px;
  border-radius: calc(1rem + 6px);
  background: var(
    --frame-gradient,
    linear-gradient(90deg, #22c55e, #16a34a, #4ade80, #10b981, #065f46)
  );
  background-size: 300% 300%;
  z-index: 1;
  animation: green-shine 3.8s linear infinite;
  pointer-events: none;
}
@keyframes green-shine {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
</style>
