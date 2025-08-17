<template>
  <aside
    class="fixed bottom-4 left-1/2 transform -translate-x-1/2 lg:left-8 lg:top-1/2 lg:bottom-auto lg:translate-x-0 lg:-translate-y-1/2 z-50"
  >
    <nav
      class="flex flex-row lg:flex-col items-center gap-3 p-2 bg-black/30 backdrop-blur-lg rounded-full border border-green-900/20 shadow-[0_10px_30px_rgba(2,6,23,0.6)]"
    >
      <div
        v-for="item in items"
        :key="item.id"
        :aria-pressed="active === item.id"
        class="group relative"
      >
        <button
          class="w-12 h-12 lg:w-14 lg:h-14 flex items-center justify-center rounded-full transition-transform duration-300 ease-out transform text-green-200 border border-transparent shadow-[0_8px_20px_rgba(4,120,87,0.12)] bg-black/20 hover:scale-110 hover:bg-gradient-to-br hover:from-green-600/80 hover:to-green-800/70 active:scale-95 focus:outline-none"
          @click="activate(item)"
          @keydown.enter.prevent="activate(item)"
        >
          <component
            :is="item.icon"
            class="w-5 h-5 lg:w-6 lg:h-6 transition-colors duration-300"
            :class="
              active === item.id
                ? 'text-white drop-shadow-[0_6px_20px_rgba(16,185,129,0.18)]'
                : 'text-green-200/90 group-hover:text-white'
            "
          />
          <span
            class="pointer-events-none absolute left-full ml-3 top-1/2 -translate-y-1/2 whitespace-nowrap rounded-lg px-3 py-2 text-sm font-semibold text-green-950 bg-gradient-to-r from-green-100 to-green-200/70 opacity-0 translate-x-1 scale-95 blur-sm transition-all duration-330 group-hover:opacity-100 group-hover:translate-x-0 group-hover:scale-100"
          >
            {{ item.label }}
          </span>
          <span
            v-if="active === item.id"
            class="absolute inset-0 rounded-full ring-2 ring-green-400/30 animate-pulse opacity-60"
          />
        </button>
      </div>
    </nav>
  </aside>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';
import { Home, Info, List, Play, Mail } from 'lucide-vue-next';

const active = ref('home');

const items = [
  { id: 'home', label: 'Home', icon: Home },
  { id: 'info', label: 'Info', icon: Info },
  { id: 'recommendations', label: 'Recommendations', icon: List },
  { id: 'demo', label: 'Demo', icon: Play },
  { id: 'contact', label: 'Contact', icon: Mail },
];

const targets = ['home', 'info', 'recommendations', 'demo', 'contact'];
const aliasMap: Record<string, string> = { 'demo-form': 'demo' };
let ticking = false;

function setActiveFromHash() {
  const h = window.location.hash.replace('#', '');
  const mapped = aliasMap[h] || h;
  if (targets.includes(mapped)) {
    active.value = mapped;
  }
}

function updateActive() {
  const center = window.innerHeight / 2;
  let best = targets[0] || 'home';
  let bestDist = Number.POSITIVE_INFINITY;
  for (const id of targets) {
    const el = document.getElementById(id);
    if (!el) continue;
    const r = el.getBoundingClientRect();
    const mid = r.top + r.height / 2;
    const d = Math.abs(mid - center);
    if (d < bestDist) {
      bestDist = d;
      best = id;
    }
  }
  active.value = best;
}

function onScroll() {
  if (ticking) return;
  ticking = true;
  requestAnimationFrame(() => {
    updateActive();
    ticking = false;
  });
}

function activate(item: { id: string }) {
  active.value = item.id;
  const el = document.querySelector(`#${item.id}`);
  if (el) {
    (el as HTMLElement).scrollIntoView({ behavior: 'smooth', block: 'center' });
  }
}

onMounted(() => {
  updateActive();
  window.addEventListener('scroll', onScroll, { passive: true });
  window.addEventListener('hashchange', setActiveFromHash);
});

onUnmounted(() => {
  window.removeEventListener('scroll', onScroll);
  window.removeEventListener('hashchange', setActiveFromHash);
});
</script>

<style>
@keyframes float-slow {
  0% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-6px);
  }
  100% {
    transform: translateY(0);
  }
}
nav > div > button:hover {
  animation: float-slow 1.8s ease-in-out infinite;
}
</style>
