<template>
  <section
    id="demo"
    class="relative w-full py-20 px-6 bg-black/80"
    aria-label="Book a demo"
  >
    <div class="absolute inset-0 -z-10 pointer-events-none">
      <div
        class="absolute left-1/2 top-0 -translate-x-1/2 -translate-y-8 w-[520px] h-[520px] rounded-full bg-gradient-to-tr from-green-700/18 to-green-300/8 blur-3xl animate-orbit"
      />
      <div
        class="absolute right-0 top-24 w-[420px] h-[420px] rounded-full bg-gradient-to-br from-green-600/10 to-transparent blur-2xl animate-tilt"
      />
      <div class="absolute inset-0 bg-black/70" />
    </div>

    <div class="max-w-7xl mx-auto">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-10 items-start">
        <div class="lg:col-span-7 order-2 lg:order-1">
          <div
            class="mb-6 inline-flex items-center gap-3 px-4 py-2 rounded-full bg-black/30 text-green-200 text-sm font-semibold uppercase tracking-wide"
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
            Book a demo
          </div>

          <h2
            class="mt-4 font-extrabold leading-tight text-[2.6rem] md:text-[3.6rem] lg:text-[4.25rem] bg-clip-text text-transparent bg-gradient-to-r from-green-300 to-green-900 uppercase tracking-tight"
          >
            Meet Zyrius
          </h2>

          <p class="mt-4 text-lg text-green-200/85 max-w-3xl">
            A social tracking web app for anime and manga fans. Follow releases,
            save favorites, like posts, and connect with friends. Discover
            curated lists and real-time updates.
          </p>

          <div class="mt-8 flex flex-wrap gap-4 items-center">
            <button class="cta-primary" @click="scrollToForm">
              Request demo
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
              @click="openDocs"
            >
              Explore docs
            </button>
          </div>

          <div class="mt-8 grid grid-cols-3 gap-6 max-w-md">
            <div class="flex flex-col items-start gap-2">
              <div class="text-2xl font-extrabold text-green-50">Live</div>
              <div class="text-sm text-green-200/80">Realtime feeds</div>
            </div>
            <div class="flex flex-col items-start gap-2">
              <div class="text-2xl font-extrabold text-green-50">Profiles</div>
              <div class="text-sm text-green-200/80">Friends & communities</div>
            </div>
            <div class="flex flex-col items-start gap-2">
              <div class="text-2xl font-extrabold text-green-50">Sync</div>
              <div class="text-sm text-green-200/80">Cross-device</div>
            </div>
          </div>
        </div>

        <div class="lg:col-span-5 order-1 lg:order-2">
          <div class="card-main shadow-xl">
            <div class="card-gradient" />
            <div class="card-stripes" />
            <div class="product-hero">
              <div class="product-info">
                <div class="badge">New</div>
                <h3 class="product-title">Zyrius</h3>
                <p class="product-sub">
                  Social tracking • Watchlists • Live releases
                </p>

                <div class="product-stats">
                  <div class="stat">
                    <div class="stat-number">8k+</div>
                    <div class="stat-label">Active users</div>
                  </div>
                  <div class="stat">
                    <div class="stat-number">120k</div>
                    <div class="stat-label">Tracked titles</div>
                  </div>
                </div>

                <div class="mt-4 flex gap-3">
                  <button
                    class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-green-600 text-black font-semibold"
                    @click="scrollToForm"
                  >
                    Try live demo
                  </button>
                  <button
                    class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-black/28 text-green-200"
                    @click="scrollToInfo"
                  >
                    See features
                  </button>
                </div>
              </div>

              <div class="product-preview" aria-hidden="true">
                <div class="preview-window">
                  <div class="preview-header">
                    <span class="dot red" />
                    <span class="dot yellow" />
                    <span class="dot green" />
                  </div>
                  <ul class="preview-list">
                    <li class="preview-item">
                      <div class="title">Oshi no Ko</div>
                      <div class="meta">S2 · Episode 4 · Live</div>
                    </li>
                    <li class="preview-item">
                      <div class="title">Frieren</div>
                      <div class="meta">S2 · New release</div>
                    </li>
                    <li class="preview-item">
                      <div class="title">My Dress-Up Darling</div>
                      <div class="meta">S2 · Popular</div>
                    </li>
                  </ul>
                </div>
              </div>
            </div>

            <div class="card-footer">
              <div class="card-tags">
                <span class="tag">Comments</span>
                <span class="tag">Favorites</span>
                <span class="tag">Share</span>
              </div>
              <div class="card-cta">
                <button class="cta-primary small" @click="scrollToForm">
                  Book a demo
                </button>
              </div>
            </div>
          </div>
        </div>

        <div id="demo-form" class="lg:col-span-12 mt-12">
          <div
            class="max-w-3xl mx-auto bg-gradient-to-b from-black/50 to-black/30 rounded-2xl p-8 shadow-2xl backdrop-blur-sm"
          >
            <h3 class="font-extrabold text-2xl text-green-50 mb-2">
              Request a demo
            </h3>
            <p class="text-green-200/80 mb-6">
              Leave your name and email and we'll reach out with a personalized
              walkthrough.
            </p>

            <form
              class="grid grid-cols-1 md:grid-cols-3 gap-4 items-end"
              @submit.prevent="submit"
            >
              <div class="md:col-span-2">
                <label class="block text-sm text-green-200/80 mb-2"
                  >Name or nickname</label
                >
                <input
                  v-model="form.name"
                  type="text"
                  required
                  class="w-full px-4 py-3 rounded-lg bg-black/20 border border-green-800/20 text-green-50 focus:outline-none focus:ring-2 focus:ring-green-600"
                  placeholder="Your name or nickname"
                >
              </div>

              <div>
                <label class="block text-sm text-green-200/80 mb-2"
                  >Email</label
                >
                <input
                  v-model="form.email"
                  type="email"
                  required
                  class="w-full px-4 py-3 rounded-lg bg-black/20 border border-green-800/20 text-green-50 focus:outline-none focus:ring-2 focus:ring-green-600"
                  placeholder="you@example.com"
                >
              </div>

              <div class="md:col-span-3 mt-2 flex gap-3">
                <button type="submit" class="cta-primary">Request demo</button>
                <button
                  type="button"
                  class="inline-flex items-center gap-2 px-4 py-3 rounded-lg bg-black/28 text-green-200"
                  @click="reset"
                >
                  Reset
                </button>
                <div class="ml-auto flex items-center gap-4 text-green-200/80">
                  <span v-if="submitting" class="text-sm">Submitting...</span>
                  <span v-if="success" class="text-sm text-green-300"
                    >Request submitted. We'll contact you soon.</span
                  >
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const form = ref({ name: '', email: '' });
const submitting = ref(false);
const success = ref(false);

function validateEmail(email: string) {
  const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return re.test(email);
}

function submit() {
  if (!form.value.name || !validateEmail(form.value.email)) {
    return;
  }
  submitting.value = true;
  success.value = false;
  setTimeout(() => {
    submitting.value = false;
    success.value = true;
    form.value.name = '';
    form.value.email = '';
  }, 900);
}

function reset() {
  form.value.name = '';
  form.value.email = '';
  success.value = false;
  submitting.value = false;
}

function scrollToForm() {
  const el = document.getElementById('demo-form');
  if (el) {
    (el as HTMLElement).scrollIntoView({ behavior: 'smooth', block: 'center' });
  }
}

function openDocs() {
  window.open('https://example.com/docs', '_blank');
}

function scrollToInfo() {
  const el = document.getElementById('info');
  if (el) {
    (el as HTMLElement).scrollIntoView({ behavior: 'smooth', block: 'start' });
  }
}
</script>

<style>
html,
body,
#app {
  overflow-x: hidden;
}
.card-main {
  position: relative;
  border-radius: 1.25rem;
  overflow: hidden;
  padding: 1.2rem;
  background: linear-gradient(
    180deg,
    rgba(3, 7, 18, 0.45),
    rgba(4, 9, 22, 0.6)
  );
  box-shadow: 0 30px 60px rgba(2, 6, 23, 0.7);
  transition: transform 0.36s ease;
}
.card-main:hover {
  transform: translateY(-6px);
}
.card-gradient {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    135deg,
    rgba(34, 197, 94, 0.08),
    rgba(6, 95, 70, 0.03)
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
  animation: stripes 12s linear infinite;
}
@keyframes stripes {
  0% {
    background-position: 0 0;
  }
  100% {
    background-position: 400px 400px;
  }
}
.product-hero {
  position: relative;
  z-index: 3;
  display: grid;
  grid-template-columns: 1fr;
  gap: 1rem;
}
.product-info {
  padding: 1rem;
}
.badge {
  display: inline-block;
  padding: 0.35rem 0.6rem;
  border-radius: 9999px;
  background: rgba(0, 0, 0, 0.36);
  color: #bbf7d0;
  font-weight: 700;
  font-size: 0.75rem;
  margin-bottom: 0.6rem;
}
.product-title {
  font-size: 1.6rem;
  color: #ecfccb;
  font-weight: 800;
  letter-spacing: 0.4px;
  margin: 0.25rem 0;
}
.product-sub {
  color: rgba(220, 252, 231, 0.85);
  font-size: 0.95rem;
  opacity: 0.95;
  margin-bottom: 0.8rem;
}
.product-stats {
  display: flex;
  gap: 1rem;
  margin-top: 0.6rem;
}
.stat {
  display: flex;
  flex-direction: column;
}
.stat-number {
  font-weight: 800;
  color: #bbf7d0;
  font-size: 1.1rem;
}
.stat-label {
  color: rgba(220, 252, 231, 0.75);
  font-size: 0.85rem;
}
.product-preview {
  display: flex;
  justify-content: center;
  align-items: center;
}
.preview-window {
  width: 220px;
  border-radius: 0.75rem;
  overflow: hidden;
  background: linear-gradient(180deg, rgba(0, 0, 0, 0.45), rgba(0, 0, 0, 0.25));
  border: 1px solid rgba(255, 255, 255, 0.03);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.02);
}
.preview-header {
  height: 34px;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem;
}
.dot {
  width: 10px;
  height: 10px;
  border-radius: 9999px;
  display: inline-block;
}
.dot.red {
  background: #ff7b7b;
}
.dot.yellow {
  background: #ffd57a;
}
.dot.green {
  background: #7efc9b;
}
.preview-list {
  padding: 0.5rem;
  display: flex;
  flex-direction: column;
  gap: 0.45rem;
}
.preview-item {
  padding: 0.55rem;
  border-radius: 0.5rem;
  background: linear-gradient(90deg, rgba(255, 255, 255, 0.01), transparent);
  transition: transform 0.22s ease, background 0.22s ease;
}
.preview-item:hover {
  transform: translateY(-4px);
  background: linear-gradient(
    90deg,
    rgba(34, 197, 94, 0.03),
    rgba(255, 255, 255, 0.02)
  );
}
.preview-item .title {
  color: #ecfccb;
  font-weight: 700;
}
.preview-item .meta {
  color: rgba(220, 252, 231, 0.7);
  font-size: 0.85rem;
}

.card-footer {
  margin-top: 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
  z-index: 3;
}
.card-tags {
  display: flex;
  gap: 0.5rem;
  align-items: center;
}
.tag {
  background: rgba(255, 255, 255, 0.03);
  color: #bbf7d0;
  padding: 0.25rem 0.5rem;
  border-radius: 0.5rem;
  font-size: 0.75rem;
}
.card-cta {
  margin-left: auto;
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
.cta-primary.small {
  padding: 0.5rem 0.9rem;
  font-size: 0.9rem;
}
.cta-primary:hover {
  transform: translateY(-3px) scale(1.02);
  box-shadow: 0 18px 40px rgba(4, 120, 87, 0.22);
}

@keyframes orbit {
  0% {
    transform: translate(0, 0) rotate(0deg);
  }
  50% {
    transform: translate(14px, -18px) rotate(90deg);
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
  animation: orbit 18s linear infinite;
}
.animate-tilt {
  animation: tilt 10s ease-in-out infinite;
}

@media (min-width: 1024px) {
  .product-hero {
    grid-template-columns: 1fr 220px;
    align-items: stretch;
  }
  .product-preview {
    align-self: center;
  }
}
@media (max-width: 768px) {
  .card-main {
    padding: 0.85rem;
  }
  .preview-window {
    width: 160px;
  }
}
</style>
