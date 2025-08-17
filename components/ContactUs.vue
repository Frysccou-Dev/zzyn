<template>
    <section class="relative w-full py-20 px-6 bg-black/85" aria-label="Contact us">
        <div class="absolute inset-0 -z-10 pointer-events-none">
            <div class="absolute left-1/2 top-0 -translate-x-1/2 -translate-y-8 w-[520px] h-[520px] rounded-full bg-gradient-to-tr from-green-700/16 to-green-300/06 blur-3xl animate-orbit" />
            <div class="absolute right-0 top-28 w-[420px] h-[420px] rounded-full bg-gradient-to-br from-green-600/08 to-transparent blur-2xl animate-tilt" />
            <div class="absolute inset-0 bg-black/75" />
        </div>

        <div class="max-w-5xl mx-auto">
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-10 items-start">
                <div class="lg:col-span-6 lg:col-start-2">
                    <div class="inline-flex items-center gap-3 px-4 py-2 rounded-full bg-black/30 text-green-200 text-sm font-semibold uppercase tracking-wide">
                        <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4 text-green-300" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M12 20l9-7-9-7-9 7 9 7z"/>
                        </svg>
                        Contact
                    </div>

                    <h2 class="mt-6 font-extrabold leading-tight text-[2.4rem] md:text-[3rem] bg-clip-text text-transparent bg-gradient-to-r from-green-300 to-green-900 uppercase tracking-tight">
                        Reach out to the team
                    </h2>

                    <p class="mt-4 text-green-200/85 max-w-2xl">
                        Send us a message and we'll get back to you. Provide a name or nickname, your email, and a short subject so we can help faster.
                    </p>
                </div>

                <div class="lg:col-span-8 lg:col-start-3 mt-6 lg:mt-0">
                    <div class="bg-gradient-to-b from-black/50 to-black/30 rounded-2xl p-6 md:p-8 shadow-2xl backdrop-blur-sm">
                        <form class="grid grid-cols-1 md:grid-cols-3 gap-4" @submit.prevent="submit">
                            <div class="md:col-span-2">
                                <label class="block text-sm text-green-200/80 mb-2">Name or nickname</label>
                                <input v-model="form.name" type="text" required class="w-full px-4 py-3 rounded-lg bg-black/20 border border-green-800/20 text-green-50 focus:outline-none focus:ring-2 focus:ring-green-600 transition" placeholder="Your name or nickname" >
                            </div>

                            <div>
                                <label class="block text-sm text-green-200/80 mb-2">Email</label>
                                <input v-model="form.email" type="email" required class="w-full px-4 py-3 rounded-lg bg-black/20 border border-green-800/20 text-green-50 focus:outline-none focus:ring-2 focus:ring-green-600 transition" placeholder="you@example.com" >
                            </div>

                            <div class="md:col-span-3">
                                <label class="block text-sm text-green-200/80 mb-2">Subject</label>
                                <input v-model="form.subject" type="text" required class="w-full px-4 py-3 rounded-lg bg-black/20 border border-green-800/20 text-green-50 focus:outline-none focus:ring-2 focus:ring-green-600 transition" placeholder="Short subject" >
                            </div>

                            <div class="md:col-span-3 mt-2 flex gap-3 items-center">
                                <button type="submit" class="cta-primary" :disabled="submitting">
                                    <span v-if="!submitting">Send message</span>
                                    <span v-else>Sending...</span>
                                </button>

                                <button type="button" class="inline-flex items-center gap-2 px-4 py-3 rounded-lg bg-black/28 text-green-200" @click="reset">
                                    Reset
                                </button>

                                <div class="ml-auto text-right">
                                    <div v-if="success" class="text-sm text-green-300">Message sent. We'll contact you soon.</div>
                                    <div v-else-if="error" class="text-sm text-red-400">Please check the fields and try again.</div>
                                </div>
                            </div>
                        </form>
                        <div class="mt-6 grid grid-cols-3 gap-3">
                            <div class="p-3 rounded-lg bg-black/25 border border-green-800/12 flex items-center gap-3">
                                <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-green-300 animate-pulse-slow" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path stroke-linecap="round" stroke-linejoin="round" d="M3 8l7.89 5.26a2 2 0 0 0 2.22 0L21 8"/></svg>
                                <div class="text-sm text-green-200/80">
                                    Fast replies
                                </div>
                            </div>
                            <div class="p-3 rounded-lg bg-black/25 border border-green-800/12 flex items-center gap-3">
                                <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-green-300" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path stroke-linecap="round" stroke-linejoin="round" d="M12 20v-6"/></svg>
                                <div class="text-sm text-green-200/80">
                                    Privacy first
                                </div>
                            </div>
                            <div class="p-3 rounded-lg bg-black/25 border border-green-800/12 flex items-center gap-3">
                                <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 text-green-300" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7"/></svg>
                                <div class="text-sm text-green-200/80">
                                    Trusted by fans
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const form = ref({ name: '', email: '', subject: '' })
const submitting = ref(false)
const success = ref(false)
const error = ref(false)

function validateEmail(email: string) {
    const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
    return re.test(email)
}

function submit() {
    error.value = false
    if (!form.value.name || !validateEmail(form.value.email) || !form.value.subject) {
        error.value = true
        return
    }
    submitting.value = true
    success.value = false
    setTimeout(() => {
        submitting.value = false
        success.value = true
        form.value.name = ''
        form.value.email = ''
        form.value.subject = ''
    }, 900)
}

function reset() {
    form.value.name = ''
    form.value.email = ''
    form.value.subject = ''
    success.value = false
    error.value = false
    submitting.value = false
}
</script>

<style>
html, body, #app {
    overflow-x: hidden;
}
.cta-primary {
    display: inline-flex;
    align-items: center;
    gap: .75rem;
    padding: .75rem 1.25rem;
    border-radius: 9999px;
    background: linear-gradient(90deg,#16a34a,#065f46);
    color: #fff;
    font-weight: 600;
    box-shadow: 0 10px 30px rgba(4,120,87,0.18);
    transition: transform .22s ease, box-shadow .22s ease;
}
.cta-primary:hover {
    transform: translateY(-3px) scale(1.02);
    box-shadow: 0 18px 40px rgba(4,120,87,0.22);
}
.bg-clip-text {
    background-clip: text;
    -webkit-background-clip: text;
}
.animate-orbit {
    animation: orbit 18s linear infinite;
}
.animate-tilt {
    animation: tilt 10s ease-in-out infinite;
}
@keyframes orbit {
    0% { transform: translate(0,0) rotate(0deg); }
    50% { transform: translate(14px,-18px) rotate(90deg); }
    100% { transform: translate(0,0) rotate(360deg); }
}
@keyframes tilt {
    0% { transform: translateY(0) rotate(0deg); }
    50% { transform: translateY(-8px) rotate(4deg); }
    100% { transform: translateY(0) rotate(0deg); }
}
@keyframes pulse-slow {
    0% { transform: scale(1); opacity: 1; }
    50% { transform: scale(1.2); opacity: .6; }
    100% { transform: scale(1); opacity: 1; }
}
.animate-pulse-slow {
    animation: pulse-slow 1.8s ease-in-out infinite;
}
</style>