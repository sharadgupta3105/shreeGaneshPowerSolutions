<template>
  <main class="flex-1 bg-gray-950 text-gray-50">
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8 py-16 sm:py-24">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-16">
        <div class="flex flex-col">
          <div class="mb-8">
            <h1 class="text-4xl font-bold tracking-tighter text-white sm:text-5xl">Contact Us</h1>
            <p class="mt-4 text-lg text-gray-400">
              We're here to help with your solar energy needs. Reach out to us with any questions or
              to schedule a consultation.
            </p>
          </div>
          <div class="space-y-8">
            <div class="flex items-start gap-4">
              <div
                class="flex h-12 w-12 flex-shrink-0 items-center justify-center rounded-full bg-primary-900 text-primary-400"
              >
                <span class="material-symbols-outlined">call</span>
              </div>
              <div>
                <h3 class="text-lg font-semibold text-white">Phone</h3>
                <p class="text-gray-400">+91-9118181918</p>
              </div>
            </div>
            <div class="flex items-start gap-4">
              <div
                class="flex h-12 w-12 flex-shrink-0 items-center justify-center rounded-full bg-primary-900 text-primary-400"
              >
                <span class="material-symbols-outlined">mail</span>
              </div>
              <div>
                <h3 class="text-lg font-semibold text-white">Email</h3>
                <p class="text-gray-400">info@shreeganeshsolar.com</p>
              </div>
            </div>
            <div class="flex items-start gap-4">
              <div
                class="flex h-12 w-12 flex-shrink-0 items-center justify-center rounded-full bg-primary-900 text-primary-400"
              >
                <span class="material-symbols-outlined">location_on</span>
              </div>
              <div>
                <h3 class="text-lg font-semibold text-white">Address</h3>
                <p class="text-gray-400">Next to Hotel Ganesh, Prabhutown, Raebareli</p>
                <p class="text-gray-400">Uttar Pradesh, 229001</p>
              </div>
            </div>
            <div class="flex items-start gap-4">
              <div
                class="flex h-12 w-12 flex-shrink-0 items-center justify-center rounded-full bg-primary-900 text-primary-400"
              >
                <span class="material-symbols-outlined">schedule</span>
              </div>
              <div>
                <h3 class="text-lg font-semibold text-white">Business Hours</h3>
                <p class="text-gray-400">Monday - Friday: 9:00 AM - 8:00 PM</p>
                <p class="text-gray-400">Saturday: 10:00 AM - 8:00 PM</p>
                <p class="text-gray-400">Sunday: Closed</p>
              </div>
            </div>
          </div>
        </div>
        <div class="flex flex-col">
          <div class="rounded-2xl bg-gray-900 p-8 shadow-2xl">
            <h2 class="text-2xl font-bold text-white mb-6">Send us a message</h2>
            <form @submit.prevent="submitForm" class="space-y-6">
              <!-- Honeypot (spam trap) -->
              <input type="text" name="bot-field" class="hidden" tabindex="-1" autocomplete="off" />

              <div>
                <label class="block text-sm font-medium text-gray-300 pb-2" for="name"
                  >Your Name</label
                >
                <input
                  class="form-input block w-full rounded-xl border-gray-700 bg-gray-800 text-white placeholder-gray-500 focus:border-primary-500 focus:ring-primary-500 h-14 px-4"
                  id="name"
                  v-model="form.name"
                  name="name"
                  placeholder="Enter your name"
                  type="text"
                  required
                />
              </div>

              <div>
                <label class="block text-sm font-medium text-gray-300 pb-2" for="email"
                  >Your Email</label
                >
                <input
                  class="form-input block w-full rounded-xl border-gray-700 bg-gray-800 text-white placeholder-gray-500 focus:border-primary-500 focus:ring-primary-500 h-14 px-4"
                  id="email"
                  v-model="form.email"
                  name="email"
                  placeholder="Enter your email"
                  type="email"
                  required
                />
              </div>

              <div>
                <label class="block text-sm font-medium text-gray-300 pb-2" for="phone"
                  >Your Phone</label
                >
                <input
                  class="form-input block w-full rounded-xl border-gray-700 bg-gray-800 text-white placeholder-gray-500 focus:border-primary-500 focus:ring-primary-500 h-14 px-4"
                  id="phone"
                  v-model="form.phone"
                  name="phone"
                  placeholder="Enter your phone number"
                  type="tel"
                />
              </div>

              <div>
                <label class="block text-sm font-medium text-gray-300 pb-2" for="message"
                  >Your Message</label
                >
                <textarea
                  class="form-textarea block w-full rounded-xl border-gray-700 bg-gray-800 text-white placeholder-gray-500 focus:border-primary-500 focus:ring-primary-500 p-4"
                  id="message"
                  v-model="form.message"
                  name="message"
                  placeholder="Enter your message"
                  rows="4"
                  required
                ></textarea>
              </div>

              <div>
                <button
                  class="flex w-full cursor-pointer items-center justify-center overflow-hidden rounded-full h-12 px-6 bg-[#122118] font-bold shadow-lg transition-all hover:bg-primary-500 disabled:opacity-60 disabled:cursor-not-allowed"
                  type="submit"
                  :disabled="loading"
                >
                  {{ loading ? 'Sending...' : 'Submit' }}
                </button>
              </div>

              <!-- Success/Error messages -->
              <p v-if="success" class="text-green-600 text-sm pt-2">
                ✅ Message sent successfully!
              </p>
              <p v-if="error" class="text-red-600 text-sm pt-2">
                ❌ Failed to send. Try again later.
              </p>
            </form>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script setup>
import { reactive, ref } from 'vue'
import emailjs from '@emailjs/browser'

const form = reactive({
  name: '',
  email: '',
  phone: '',
  message: '',
})

const loading = ref(false)
const success = ref(false)
const error = ref(false)

const submitForm = () => {
  loading.value = true
  success.value = false
  error.value = false

  emailjs
    .send(
      'service_0s6nf6q', // <-- replace with your service ID
      'template_keppagk', // <-- replace with your template ID
      form,
      'LavZxzQtEbGe--I14', // <-- replace with your public key
    )
    .then(() => {
      success.value = true
      loading.value = false
      Object.keys(form).forEach((k) => (form[k] = '')) // reset form
    })
    .catch(() => {
      error.value = true
      loading.value = false
    })
}
</script>

<style type="text/tailwindcss">
:root {
  --primary-50: #f0fdf6;
  --primary-100: #dcfce9;
  --primary-200: #bbf7d4;
  --primary-300: #86efb5;
  --primary-400: #4ade8f;
  --primary-500: #22c56a;
  --primary-600: #16a354;
  --primary-700: #158046;
  --primary-800: #16653b;
  --primary-900: #145331;
  --primary-950: #0a2e19;
}
</style>
