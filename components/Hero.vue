<template>
  <section
    class="relative w-full min-h-screen flex items-center z-10 overflow-hidden"
    aria-label="Main hero"
  >
    <div class="absolute inset-0 z-0 pointer-events-none decor-clip">
      <div
        class="absolute decor-left -top-44 w-[520px] h-[520px] rounded-full bg-gradient-to-tr from-green-700/28 to-green-300/12 blur-3xl animate-orbit"
      />
      <div
        class="absolute decor-right top-16 w-[460px] h-[460px] rounded-full bg-gradient-to-br from-pink-500/14 to-purple-600/08 blur-2xl animate-tilt"
      />
      <div class="absolute inset-0 bg-black/56 backdrop-blur-sm" />
    </div>

    <div class="container mx-auto px-6 py-28 relative z-10">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-10 items-start">
        <div class="lg:col-span-7 text-center lg:text-left">
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
            Curated recommendations
          </p>

          <h1
            class="mt-6 font-extrabold leading-tight text-[3.2rem] md:text-[4rem] lg:text-[5rem] bg-clip-text text-transparent bg-gradient-to-r from-green-300 to-green-900 uppercase tracking-tight"
          >
            zzyn
          </h1>

          <div class="mt-4 text-lg md:text-xl text-green-200/90 max-w-3xl">
            <span class="inline-block mr-3 opacity-80"
              >Relax • Discover • Vibe</span
            >
            <span
              class="inline-block text-green-50 font-semibold typing"
              aria-hidden="true"
              >{{ typed }}</span
            >
          </div>

          <p class="mt-6 text-green-200/80 max-w-2xl">
            A corner for tired developers to unwind with handpicked anime and
            manga. Find titles for every mood and moment.
          </p>

          <div class="mt-8 flex flex-wrap gap-4 items-center">
            <button class="cta-primary" @click="scrollTo('#recommendations')">
              Explore recommendations
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
            </button>

            <button
              class="inline-flex items-center gap-2 px-5 py-3 rounded-full bg-black/30 text-green-200 hover:bg-black/40 transition"
              @click="scrollTo('#info')"
            >
              Learn more
            </button>

            <div class="ml-2 flex items-center gap-3">
              <div
                class="px-3 py-1 rounded-full bg-black/30 text-green-200 text-sm"
              >
                Free
              </div>
              <div
                class="px-3 py-1 rounded-full bg-black/30 text-green-200 text-sm"
              >
                Curated
              </div>
              <div
                class="px-3 py-1 rounded-full bg-black/30 text-green-200 text-sm"
              >
                Updated
              </div>
            </div>
          </div>

          <div class="mt-8 grid grid-cols-3 gap-4 max-w-md">
            <div class="flex flex-col items-start gap-2">
              <div class="text-2xl font-extrabold text-green-50">120+</div>
              <div class="text-sm text-green-200/80">Handpicked titles</div>
            </div>
            <div class="flex flex-col items-start gap-2">
              <div class="text-2xl font-extrabold text-green-50">5</div>
              <div class="text-sm text-green-200/80">Featured categories</div>
            </div>
            <div class="flex flex-col items-start gap-2">
              <div class="text-2xl font-extrabold text-green-50">24/7</div>
              <div class="text-sm text-green-200/80">Accessible</div>
            </div>
          </div>
        </div>

        <div class="lg:col-span-5 flex justify-center lg:justify-end">
          <div class="relative w-full max-w-[520px]">
            <div class="card-main">
              <img
                src="/cote-banner.jpg"
                alt="Oshi no Ko cover"
                class="card-image"
              />
              <div class="card-gradient" />
              <div class="card-stripes" />
              <div class="card-content">
                <div class="card-badge">New</div>
                <h3 class="card-title">Classroom of the Elite</h3>
                <p class="card-sub">Thriller · Mystery · Impactful</p>
                <div class="card-tags">
                  <span class="tag">Thriller</span>
                  <span class="tag">Psychological</span>
                  <span class="tag">Popular</span>
                </div>
              </div>
            </div>

            <div
              class="absolute -bottom-6 left-4 flex items-center gap-3 bg-black/40 border border-green-800/20 px-3 py-2 rounded-full text-green-200 shadow-md"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="w-5 h-5 text-green-300"
                viewBox="0 0 24 24"
                fill="none"
                stroke="currentColor"
                stroke-width="1.5"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M12 6v6l4 2"
                />
              </svg>
              <span class="text-sm">New 4th Season</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

const phrases = ['to unwind', 'to laugh', 'to ponder', 'to be moved'];
const typed = ref('');
let idx = 0;
let char = 0;
let forward = true;
let interval: number | undefined;

function tick() {
  const current = phrases[idx] ?? '';
  if (forward) {
    typed.value = current.slice(0, char + 1);
    char++;
    if (char === current.length) {
      forward = false;
      clearTick();
      interval = window.setTimeout(() => {
        interval = window.setInterval(tick, 80);
      }, 900);
    }
  } else {
    typed.value = current.slice(0, Math.max(0, char - 1));
    char--;
    if (char === 0) {
      forward = true;
      idx = (idx + 1) % phrases.length;
    }
  }
}

function clearTick() {
  if (interval) {
    clearInterval(interval);
  }
}

onMounted(() => {
  interval = window.setInterval(tick, 80);
});

onUnmounted(() => {
  clearTick();
});

function scrollTo(selector: string) {
  const el = document.querySelector(selector);
  if (el) {
    (el as HTMLElement).scrollIntoView({ behavior: 'smooth', block: 'start' });
  }
}

defineOptions({ name: 'AppHero' });
</script>

<style>
html,
body,
#app {
  overflow-x: hidden;
}
.decor-clip {
  overflow: hidden;
}
.decor-left,
.decor-right {
  left: 50%;
  transform: translateX(-50%);
}
@media (min-width: 1024px) {
  .decor-left {
    left: -40px;
    transform: none;
  }
  .decor-right {
    left: auto;
    right: -120px;
    transform: none;
  }
}
.container {
  max-width: 1200px;
  margin-inline: auto;
}
@keyframes orbit {
  0% {
    transform: translate(0, 0) rotate(0deg);
  }
  50% {
    transform: translate(18px, -20px) rotate(90deg);
  }
  100% {
    transform: translate(0, 0) rotate(360deg);
  }
}
@keyframes tilt {
  0% {
    transform: translateY(0) rotate(0deg);
  }
  50% {
    transform: translateY(-8px) rotate(4deg);
  }
  100% {
    transform: translateY(0) rotate(0deg);
  }
}
.animate-orbit {
  animation: orbit 16s linear infinite;
}
.animate-tilt {
  animation: tilt 10s ease-in-out infinite;
}
.typing::after {
  content: '|';
  opacity: 0.9;
  margin-left: 6px;
  animation: blink 1s steps(2, start) infinite;
}
@keyframes blink {
  0% {
    opacity: 1;
  }
  50% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
.cta-primary {
  display: inline-flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.75rem 1.25rem;
  border-radius: 9999px;
  background: linear-gradient(90deg, #16a34a, #065f46);
  color: #fff;
  font-weight: 600;
  box-shadow: 0 10px 30px rgba(4, 120, 87, 0.18);
  transition: transform 0.22s ease, box-shadow 0.22s ease;
}
.cta-primary:hover {
  transform: translateY(-3px) scale(1.02);
  box-shadow: 0 18px 40px rgba(4, 120, 87, 0.22);
}
.card-main {
  position: relative;
  width: 100%;
  aspect-ratio: 4/5;
  border-radius: 1.25rem;
  overflow: hidden;
  box-shadow: 0 20px 50px rgba(2, 6, 23, 0.6);
  transition: transform 0.48s cubic-bezier(0.2, 0.9, 0.2, 1);
  background: linear-gradient(
    180deg,
    rgba(3, 7, 18, 0.5),
    rgba(4, 9, 22, 0.65)
  );
}
.card-main:hover {
  transform: translateY(-6px) scale(1.01);
}
.card-gradient {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    135deg,
    rgba(34, 197, 94, 0.1),
    rgba(6, 95, 70, 0.04)
  );
  z-index: 1;
}
.card-stripes {
  position: absolute;
  inset: 0;
  background-image: repeating-linear-gradient(
    -45deg,
    rgba(255, 255, 255, 0.02) 0 6px,
    transparent 6px 18px
  );
  mix-blend-mode: overlay;
  opacity: 0.9;
  z-index: 2;
  animation: stripes 10s linear infinite;
}
@keyframes stripes {
  0% {
    background-position: 0 0;
  }
  100% {
    background-position: 300px 300px;
  }
}
.card-content {
  position: relative;
  z-index: 3;
  padding: 1.25rem;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  justify-content: flex-end;
  height: 100%;
}
.card-badge {
  background: rgba(0, 0, 0, 0.36);
  color: #bbf7d0;
  padding: 0.35rem 0.6rem;
  border-radius: 9999px;
  font-weight: 700;
  font-size: 0.75rem;
  width: max-content;
  backdrop-filter: blur(4px);
}
.card-title {
  font-size: 1.45rem;
  color: #ecfccb;
  font-weight: 800;
  letter-spacing: 0.6px;
  margin-top: 0.25rem;
}
.card-sub {
  color: rgba(220, 252, 231, 0.85);
  font-size: 0.9rem;
  opacity: 0.95;
}
.card-tags {
  margin-top: 0.6rem;
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
}
.tag {
  background: rgba(255, 255, 255, 0.03);
  color: #bbf7d0;
  padding: 0.25rem 0.5rem;
  border-radius: 0.5rem;
  font-size: 0.75rem;
}
.stacked-mini {
  margin-right: 0.25rem;
}
.mini-card {
  background: linear-gradient(
    90deg,
    rgba(255, 255, 255, 0.02),
    rgba(255, 255, 255, 0.01)
  );
  color: #d1fae5;
  padding: 0.55rem 0.85rem;
  border-radius: 0.75rem;
  font-weight: 700;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.45);
  transition: transform 0.32s ease;
}
.mini-card:hover {
  transform: translateY(-6px);
}
@media (max-width: 1024px) {
  .h1 {
    font-size: 3.2rem;
  }
  .card-main {
    max-width: 420px;
    margin-inline: auto;
  }
}
.card-image {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  z-index: 0;
  opacity: 1;
  filter: brightness(0.3);
  transition: transform 0.6s cubic-bezier(0.2, 0.9, 0.2, 1), filter 0.45s ease;
}
.card-main:hover .card-image {
  transform: scale(1.03);
  filter: brightness(0.85);
}
section[aria-label='Main hero'] {
  max-width: 100vw;
  overflow-x: hidden;
}
</style>
