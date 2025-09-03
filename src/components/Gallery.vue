<template>
  <main class="flex-1">
    <section class="py-16 sm:py-24 relative">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-12">
          <h2 class="text-4xl sm:text-5xl font-bold tracking-tight text-white">
            Our Project Gallery
          </h2>
          <p class="mt-4 max-w-2xl mx-auto text-lg text-[#96c5a9]">
            Explore our portfolio of successful solar installations across residential, commercial,
            and healthcare sectors.
          </p>
        </div>

        <div class="relative overflow-hidden">
          <!-- Slide Track -->
          <div
            class="flex transition-transform duration-700 ease-in-out"
            :style="{ transform: `translateX(-${currentSlide * 100}%)` }"
          >
            <!-- Each Slide -->
            <div
              v-for="(slide, sIndex) in slides"
              :key="sIndex"
              class="w-full flex-shrink-0 grid gap-6"
              :class="{
                'grid-cols-1': visibleCols === 1,
                'grid-cols-2': visibleCols === 2,
                'grid-cols-3': visibleCols === 3,
              }"
            >
              <div
                v-for="(item, index) in slide"
                :key="index"
                class="group relative overflow-hidden rounded-xl shadow-lg"
              >
                <div
                  class="w-full h-64 bg-center bg-no-repeat bg-cover transition-transform duration-500 group-hover:scale-105"
                  :style="{ backgroundImage: `url(${item.image})` }"
                ></div>
                <div class="absolute inset-0 bg-gradient-to-t from-black/70 to-transparent"></div>
                <div class="absolute bottom-0 left-0 p-6">
                  <h3 class="text-xl font-semibold text-white">{{ item.title }}</h3>
                  <p class="text-sm text-gray-300 mt-1">{{ item.subtitle }}</p>
                </div>
              </div>
            </div>
          </div>

          <!-- Prev Button -->
          <button
            @click="prevSlide"
            class="absolute top-1/2 left-4 -translate-y-1/2 bg-white text-black shadow-lg hover:bg-gray-200 w-10 h-10 flex items-center justify-center rounded-full z-10"
          >
            ‹
          </button>

          <!-- Next Button -->
          <button
            @click="nextSlide"
            class="absolute top-1/2 right-4 -translate-y-1/2 bg-white text-black shadow-lg hover:bg-gray-200 w-10 h-10 flex items-center justify-center rounded-full z-10"
          >
            ›
          </button>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup>
import { ref, computed, onMounted, onBeforeUnmount, watch } from 'vue'

// Helper to resolve images from assets (Vite / Vue)
const resolveImage = (filename) => new URL(`../assets/${filename}`, import.meta.url).href

// Gallery items (25 images)
const galleryItems = [
  {
    image: resolveImage('1.jpg'),
    title: 'Residential Installation',
    subtitle: 'Private home, RaeBareli',
  },
  {
    image: resolveImage('2.jpg'),
    title: 'Commercial Project',
    subtitle: 'Office Building, Raebareli',
  },
  {
    image: resolveImage('3.jpg'),
    title: 'Residential Installation',
    subtitle: 'City Hospital, Raebareli',
  },
  {
    image: resolveImage('4.jpg'),
    title: 'Residential Installation',
    subtitle: 'Modern Villa, Raebareli',
  },
  {
    image: resolveImage('5.jpg'),
    title: 'Commercial Project',
    subtitle: 'Factory Rooftop, Raebareli',
  },
  {
    image: resolveImage('6.jpg'),
    title: 'Residential Installation',
    subtitle: 'Community Clinic, Raebareli',
  },
  {
    image: resolveImage('7.jpg'),
    title: 'Residential Installation',
    subtitle: 'Private home, Raebareli',
  },
  {
    image: resolveImage('8.jpg'),
    title: 'Commercial Project',
    subtitle: 'Shopping Mall, Raebareli',
  },
  {
    image: resolveImage('9.jpg'),
    title: 'Residential Installation',
    subtitle: 'Medical Center, Raebareli',
  },
  {
    image: resolveImage('10.jpg'),
    title: 'Residential Installation',
    subtitle: 'Farmhouse, Raebareli',
  },
  { image: resolveImage('11.jpg'), title: 'Commercial Project', subtitle: 'Tech Park, Bangalore' },
  {
    image: resolveImage('12.jpg'),
    title: 'Residential Installation',
    subtitle: 'Children’s Hospital, Raebareli',
  },
  {
    image: resolveImage('13.jpg'),
    title: 'Residential Installation',
    subtitle: 'Apartment Complex, Raebareli',
  },
  {
    image: resolveImage('14.jpg'),
    title: 'Commercial Project',
    subtitle: 'Corporate Office, Raebareli',
  },
  {
    image: resolveImage('15.jpg'),
    title: 'Residential Installation',
    subtitle: 'General Hospital, Lucknow',
  },
  {
    image: resolveImage('16.jpg'),
    title: 'Residential Installation',
    subtitle: 'Bungalow, Raebareli',
  },
  { image: resolveImage('17.jpg'), title: 'Commercial Project', subtitle: 'Warehouse, Raebareli' },
  {
    image: resolveImage('18.jpg'),
    title: 'Residential Installation',
    subtitle: 'Specialty Clinic, Raebareli',
  },
  {
    image: resolveImage('19.jpg'),
    title: 'Residential Installation',
    subtitle: 'Luxury Villa, Raebareli',
  },
  {
    image: resolveImage('20.jpg'),
    title: 'Commercial Project',
    subtitle: 'Hotel Rooftop, Raebareli',
  },
  {
    image: resolveImage('21.jpg'),
    title: 'Residential Installation',
    subtitle: 'City Hospital, Raebareli',
  },
  {
    image: resolveImage('22.jpg'),
    title: 'Residential Installation',
    subtitle: 'Townhouse, Raebareli',
  },
  {
    image: resolveImage('23.jpg'),
    title: 'Commercial Project',
    subtitle: 'Industrial Plant, Raebareli',
  },
  {
    image: resolveImage('24.jpg'),
    title: 'Residential Installation',
    subtitle: 'Care Center, Raebareli',
  },
  //   {
  //     image: resolveImage('25.jpg'),
  //     title: 'Residential Installation',
  //     subtitle: 'Private Villa, Mysore',
  //   },
]

// slider state
const currentSlide = ref(0)
const visibleCols = ref(3) // 1 (mobile), 2 (tablet), 3 (desktop)
const rows = 2

// responsive handling
const updateCols = () => {
  if (window.innerWidth < 640) {
    visibleCols.value = 1
  } else if (window.innerWidth < 1024) {
    visibleCols.value = 2
  } else {
    visibleCols.value = 3
  }
}

// create slides: chunk into pages of (visibleCols * rows)
const slides = computed(() => {
  const perSlide = visibleCols.value * rows
  const chunks = []
  for (let i = 0; i < galleryItems.length; i += perSlide) {
    chunks.push(galleryItems.slice(i, i + perSlide))
  }
  // if last chunk is smaller, it's fine — it will still render
  return chunks
})

const totalSlides = computed(() => slides.value.length)

// Navigation
const nextSlide = () => {
  if (totalSlides.value === 0) return
  currentSlide.value = (currentSlide.value + 1) % totalSlides.value
}
const prevSlide = () => {
  if (totalSlides.value === 0) return
  currentSlide.value = (currentSlide.value - 1 + totalSlides.value) % totalSlides.value
}

// Auto-slide interval management
let autoInterval = null

function startAutoSlide() {
  stopAutoSlide()
  // only start if we have more than one slide
  if (totalSlides.value > 1) {
    autoInterval = setInterval(() => {
      nextSlide()
    }, 5000)
  }
}

function stopAutoSlide() {
  if (autoInterval) {
    clearInterval(autoInterval)
    autoInterval = null
  }
}

// Reset currentSlide if slides count decreases (prevent out-of-bounds)
watch(slides, (newSlides) => {
  if (currentSlide.value >= newSlides.length) {
    currentSlide.value = 0
  }
  // restart auto-slide so interval timing stays consistent
  startAutoSlide()
})

// handle resize & lifecycle
onMounted(() => {
  updateCols()
  window.addEventListener('resize', updateCols)
  startAutoSlide()
})

onBeforeUnmount(() => {
  window.removeEventListener('resize', updateCols)
  stopAutoSlide()
})
</script>
