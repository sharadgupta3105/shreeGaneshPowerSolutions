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
                <p class="text-gray-400">400001, Mumbai, India</p>
                <p class="text-gray-400">Maharashtra</p>
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
                <p class="text-gray-400">Monday - Friday: 9:00 AM - 6:00 PM</p>
                <p class="text-gray-400">Saturday: 10:00 AM - 4:00 PM</p>
                <p class="text-gray-400">Sunday: Closed</p>
              </div>
            </div>
          </div>
        </div>
        <div class="flex flex-col">
          <div class="rounded-2xl bg-gray-900 p-8 shadow-2xl">
            <h2 class="text-2xl font-bold text-white mb-6">Send us a message</h2>
            <form action="#" class="space-y-6" method="POST">
              <div>
                <label class="block text-sm font-medium text-gray-300 pb-2" for="name"
                  >Your Name</label
                >
                <input
                  class="form-input block w-full rounded-xl border-gray-700 bg-gray-800 text-white placeholder-gray-500 focus:border-primary-500 focus:ring-primary-500 h-14 px-4"
                  id="name"
                  name="name"
                  placeholder="Enter your name"
                  type="text"
                />
              </div>
              <div>
                <label class="block text-sm font-medium text-gray-300 pb-2" for="email"
                  >Your Email</label
                >
                <input
                  class="form-input block w-full rounded-xl border-gray-700 bg-gray-800 text-white placeholder-gray-500 focus:border-primary-500 focus:ring-primary-500 h-14 px-4"
                  id="email"
                  name="email"
                  placeholder="Enter your email"
                  type="email"
                />
              </div>
              <div>
                <label class="block text-sm font-medium text-gray-300 pb-2" for="phone"
                  >Your Phone</label
                >
                <input
                  class="form-input block w-full rounded-xl border-gray-700 bg-gray-800 text-white placeholder-gray-500 focus:border-primary-500 focus:ring-primary-500 h-14 px-4"
                  id="phone"
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
                  name="message"
                  placeholder="Enter your message"
                  rows="4"
                ></textarea>
              </div>
              <div>
                <button
                  class="flex w-full cursor-pointer items-center justify-center overflow-hidden rounded-full h-12 px-6 bg-[#122118] font-bold shadow-lg transition-all hover:bg-primary-500"
                  type="submit"
                >
                  Submit
                </button>
              </div>
            </form>
          </div>
        </div>
      </div>
      <div class="mt-16 sm:mt-24">
        <div
          class="w-full h-96 rounded-2xl bg-center bg-no-repeat bg-cover object-cover shadow-2xl"
          style="
            background-image: url('https://lh3.googleusercontent.com/aida-public/AB6AXuBzMoi4gGZcCUaZzr7lBBc8poo9aXxWdMlorvi3J6KQJwg5KFfJuG-Lz0JGn-RUz9o6tnRpiPQ0iQe0eNtElriePMNFYuepH4_0LeuRjwgPb8b3pvRNuC_GBbcP4TLkI9ct7Vvd917qaUVSJYYiGMpbBibpHyBP7QVuVW5SRIlS12KtpM9u9XL8T5S6opChTMUZTXDuBpqhVBd1KYezjy5eOaYPgiSgx5SoNXaTsWklxLzuib6SIACbYZnBLjE6ghIcyWTn-TzL0rc');
          "
        ></div>
      </div>
    </div>
  </main>
</template>

<script>
export default {}
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
