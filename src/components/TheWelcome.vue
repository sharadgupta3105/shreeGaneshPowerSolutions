<template>
  <div
    class="relative flex size-full min-h-screen flex-col dark group/design-root overflow-x-hidden"
  >
    <div class="layout-container flex h-full grow flex-col">
      <header class="sticky top-0 z-50 bg-[#213e2c]/80 backdrop-blur-sm">
        <div
          class="mx-auto flex max-w-7xl items-center justify-between whitespace-nowrap px-6 md:px-10 py-4"
        >
          <!-- Logo -->
          <a
            class="flex items-center gap-3 text-white cursor-pointer"
            @click="scrollToSection('top')"
          >
            <span class="material-symbols-outlined text-3xl text-[#38e07b]">bolt</span>
            <h2 class="text-white text-lg sm:text-xl font-bold leading-tight tracking-[-0.015em]">
              Shree Ganesh Power Solutions
            </h2>
          </a>

          <!-- Desktop Nav -->
          <nav class="hidden md:flex items-center gap-8">
            <button
              v-for="link in links"
              :key="link.id"
              @click="scrollToSection(link.id)"
              class="text-gray-300 hover:text-white transition-colors text-sm font-medium leading-normal"
            >
              {{ link.label }}
            </button>
          </nav>

          <!-- Desktop CTA -->
          <button
            @click="scrollToSection('contact')"
            class="hidden md:flex min-w-[84px] cursor-pointer items-center justify-center overflow-hidden rounded-full h-10 px-6 bg-[#38e07b] hover:bg-[#32c76e] transition-colors text-[#213e2c] text-sm font-bold leading-normal tracking-[0.015em]"
          >
            <span class="truncate">Get a Quote</span>
          </button>

          <!-- Mobile Menu Button -->
          <button
            @click="isOpen = !isOpen"
            class="md:hidden text-white text-3xl"
            aria-label="Toggle Menu"
          >
            <span class="material-symbols-outlined">
              {{ isOpen ? 'close' : 'menu' }}
            </span>
          </button>
        </div>

        <!-- Mobile Menu -->
        <transition name="slide">
          <nav v-if="isOpen" class="md:hidden bg-[#213e2c] px-6 py-4 flex flex-col gap-4">
            <button
              v-for="link in links"
              :key="link.id"
              @click="scrollToSection(link.id)"
              class="text-gray-300 hover:text-white transition-colors text-base font-medium text-left"
            >
              {{ link.label }}
            </button>
            <button
              @click="scrollToSection('contact')"
              class="w-full text-center rounded-full bg-[#38e07b] hover:bg-[#32c76e] transition-colors text-[#213e2c] text-sm font-bold py-2"
            >
              Get a Quote
            </button>
          </nav>
        </transition>
      </header>
      <main class="flex-1">
        <section
          class="relative flex min-h-[75vh] items-center justify-center bg-cover bg-center bg-no-repeat"
          style="
            background-image:
              linear-gradient(rgba(0, 0, 0, 0.1) 0%, #213e2c 100%),
              url('https://lh3.googleusercontent.com/aida-public/AB6AXuCFvMoqXnCpquinTm9RdSZzDoYBvf38jvSib_P5vxhJ57VJpgOSetwreTJ7rGbJMfNER8QsoS9l4Gq_uMGsC9Jxkd-6RnIk3gHwoTepa54_k5JdiP6_bgb8uUA7RpyitFoE83f5WiUwxChdqdarItmF_P1UpAwtMGZgWk7Z8LN1kwOIyyrAVXB_ipwD3QkCAntKYHDVyWn9MryQ33luDVxqjNNvm1GXm9Y-LFZii8tkeDtStq3T00QdHE2SH46vKL48gLhhlHQ09B8');
          "
        >
          <div class="relative z-20 flex flex-col gap-6 text-center max-w-4xl px-4">
            <h1 class="text-white text-5xl font-black leading-tight tracking-tight md:text-6xl">
              Empowering Your Future with Sustainable Energy
            </h1>
            <p class="text-gray-200 text-lg md:text-xl">
              Shree Ganesh Power Solutions is your trusted partner for solar energy solutions. We
              provide reliable and efficient solar installations tailored to your needs.
            </p>
            <div class="flex justify-center">
              <button
                @click="scrollToSection('contact')"
                class="flex min-w-[84px] max-w-[480px] cursor-pointer items-center justify-center overflow-hidden rounded-lg h-12 px-8 bg-[#38e07b] text-[#0e1a13] text-base font-bold leading-normal tracking-[0.015em] hover:bg-green-500/90 transition-colors"
              >
                <span class="truncate">Get a Quote</span>
              </button>
            </div>
          </div>
        </section>
        <section class="py-20 sm:py-28">
          <div class="mx-auto max-w-7xl px-4 sm:px-10">
            <div class="text-center max-w-3xl mx-auto">
              <h2 class="text-white text-4xl font-bold tracking-tight md:text-5xl">Our Services</h2>
              <p class="mt-4 text-lg text-gray-400">
                We offer comprehensive solar solutions tailored to meet the unique needs of various
                sectors.
              </p>
            </div>
            <div class="mt-16 grid grid-cols-1 gap-8 md:grid-cols-3">
              <div
                class="flex flex-col gap-4 rounded-2xl border border-[#366348] bg-[#1b3124] p-8 transition-all hover:border-[#38e07b] hover:shadow-2xl hover:shadow-[#38e07b]/10"
              >
                <span class="material-symbols-outlined text-4xl text-[#38e07b]"> home </span>
                <div class="flex flex-col gap-1">
                  <h3 class="text-white text-xl font-bold leading-tight">Residential Solar</h3>
                  <p class="text-[#96c5a9] text-base font-normal leading-normal">
                    Power your home with clean, renewable energy and reduce your electricity bills.
                  </p>
                </div>
              </div>
              <div
                class="flex flex-col gap-4 rounded-2xl border border-[#366348] bg-[#1b3124] p-8 transition-all hover:border-[#38e07b] hover:shadow-2xl hover:shadow-[#38e07b]/10"
              >
                <span class="material-symbols-outlined text-4xl text-[#38e07b]">
                  business_center
                </span>
                <div class="flex flex-col gap-1">
                  <h3 class="text-white text-xl font-bold leading-tight">Commercial Solar</h3>
                  <p class="text-[#96c5a9] text-base font-normal leading-normal">
                    Optimize your business operations with sustainable energy solutions and lower
                    operating costs.
                  </p>
                </div>
              </div>
              <div
                class="flex flex-col gap-4 rounded-2xl border border-[#366348] bg-[#1b3124] p-8 transition-all hover:border-[#38e07b] hover:shadow-2xl hover:shadow-[#38e07b]/10"
              >
                <span class="material-symbols-outlined text-4xl text-[#38e07b]">
                  local_hospital
                </span>
                <div class="flex flex-col gap-1">
                  <h3 class="text-white text-xl font-bold leading-tight">Hospital Solar</h3>
                  <p class="text-[#96c5a9] text-base font-normal leading-normal">
                    Ensure uninterrupted power supply for critical healthcare facilities with
                    reliable solar systems.
                  </p>
                </div>
              </div>
            </div>
          </div>
        </section>
        <section class="py-20 sm:py-28 bg-[#213e2c]">
          <div class="mx-auto max-w-7xl px-4 sm:px-10">
            <div class="grid grid-cols-1 items-center gap-12 lg:grid-cols-2">
              <div class="flex flex-col items-start gap-6">
                <div class="inline-block rounded-full bg-[#1b3124] px-4 py-2">
                  <p class="text-sm font-medium text-[#38e07b]">Government Scheme</p>
                </div>
                <h2 class="text-4xl font-bold tracking-tight text-white md:text-5xl">
                  PM Surya Ghar Yojana
                </h2>
                <p class="text-lg text-gray-400">
                  Harness the power of the sun with the 'PM Surya Ghar Yojana' and enjoy substantial
                  savings on your electricity bills. This government initiative aims to promote
                  renewable energy by providing financial assistance for rooftop solar
                  installations.
                </p>
                <div class="space-y-4">
                  <div class="flex items-start gap-4">
                    <span class="material-symbols-outlined mt-1 text-2xl text-[#38e07b]"
                      >check_circle</span
                    >
                    <div>
                      <h3 class="text-lg font-bold text-white">Subsidy Benefits</h3>
                      <p class="text-gray-400">
                        Receive up to 78,000 INR in government subsidy for installing a rooftop
                        solar system.
                      </p>
                    </div>
                  </div>
                  <div class="flex items-start gap-4">
                    <span class="material-symbols-outlined mt-1 text-2xl text-[#38e07b]"
                      >check_circle</span
                    >
                    <div>
                      <h3 class="text-lg font-bold text-white">Expert Assistance</h3>
                      <p class="text-gray-400">
                        Shree Ganesh Power Solutions provides end-to-end support, from application
                        to installation, ensuring you maximize the scheme's benefits.
                      </p>
                    </div>
                  </div>
                  <div class="flex items-start gap-4">
                    <span class="material-symbols-outlined mt-1 text-2xl text-[#38e07b]"
                      >check_circle</span
                    >
                    <div>
                      <h3 class="text-lg font-bold text-white">Free Electricity</h3>
                      <p class="text-gray-400">
                        Generate up to 300 units of free electricity per month, reducing your
                        dependency on the grid.
                      </p>
                    </div>
                  </div>
                </div>
                <a
                  class="mt-4 inline-flex min-w-[84px] max-w-[480px] cursor-pointer items-center justify-center overflow-hidden rounded-full h-12 px-8 bg-[#38e07b] text-base font-bold leading-normal tracking-[0.015em] text-[#213e2c] transition-colors hover:bg-[#32c76e]"
                  href="#contact"
                >
                  <span class="truncate">Learn More &amp; Apply</span>
                </a>
              </div>
              <div class="h-full w-full">
                <img
                  alt="Solar panels on a rooftop"
                  class="h-full w-full rounded-2xl object-cover"
                  src="../assets/PMsurya.jpg"
                />
              </div>
            </div>
          </div>
        </section>
        <section id="services">
          <our-services />
        </section>
        <section id="about">
          <about-us />
        </section>
        <section id="gallery">
          <gallery />
        </section>
        <section id="contact">
          <contact-us />
        </section>
      </main>
      <footer class="border-t border-[#264532] py-10">
        <div class="mx-auto max-w-7xl px-4 sm:px-10">
          <div class="flex flex-col items-center justify-between gap-6 md:flex-row">
            <div class="flex items-center gap-3 text-white">
              <span class="material-symbols-outlined text-2xl text-[#38e07b]">bolt</span>
              <h2 class="text-white text-lg font-bold">Shree Ganesh Power Solutions</h2>
            </div>
            <nav class="flex flex-wrap items-center justify-center gap-6">
              <a
                class="text-gray-400 hover:text-white transition-colors text-sm font-medium"
                href="#services"
                >Services</a
              >
              <a
                class="text-gray-400 hover:text-white transition-colors text-sm font-medium"
                href="#about"
                >About Us</a
              >
              <a
                class="text-gray-400 hover:text-white transition-colors text-sm font-medium"
                href="#gallery"
                >Gallery</a
              >
              <a
                class="text-gray-400 hover:text-white transition-colors text-sm font-medium"
                href="#contact"
                >Contact Us</a
              >
            </nav>
            <p class="text-gray-500 text-sm">
              © 2024 Shree Ganesh Power Solutions. All rights reserved.
            </p>
          </div>
        </div>
      </footer>
    </div>
  </div>
</template>

<script setup>
import OurServices from './OurServices.vue'
import AboutUs from './AboutUs.vue'
import Gallery from './Gallery.vue'
import ContactUs from './ContactUs.vue'
import { ref } from 'vue'

const isOpen = ref(false)

const links = [
  { id: 'services', label: 'Services' },
  { id: 'about', label: 'About Us' },
  { id: 'gallery', label: 'Gallery' },
  { id: 'contact', label: 'Contact Us' },
]

function scrollToSection(id) {
  const section = document.getElementById(id)
  if (section) {
    section.scrollIntoView({ behavior: 'smooth', block: 'start' })
    isOpen.value = false // close mobile menu after click
  }
}
</script>

<style>
/* Slide down animation for mobile nav */
.slide-enter-active,
.slide-leave-active {
  transition: all 0.3s ease;
}
.slide-enter-from,
.slide-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
