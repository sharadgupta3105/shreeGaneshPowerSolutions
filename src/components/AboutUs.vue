<template>
  <main class="flex flex-1 flex-col items-center py-16 sm:py-24">
    <div class="container mx-auto px-4 sm:px-6 lg:px-8">
      <div class="max-w-4xl mx-auto text-center">
        <h1
          class="text-4xl font-extrabold tracking-tighter sm:text-5xl lg:text-6xl text-transparent bg-clip-text bg-gradient-to-r from-white to-[var(--primary-color)]"
        >
          About Us
        </h1>
        <p class="mt-6 text-lg text-gray-300">
          Empowering a sustainable future with clean, reliable solar energy.
        </p>
      </div>
      <div class="mt-16 grid grid-cols-1 gap-12 md:grid-cols-2 md:gap-16">
        <div class="space-y-8">
          <div>
            <h2 class="text-2xl font-bold tracking-tight text-[var(--primary-color)]">
              Our Mission
            </h2>
            <p class="mt-4 text-gray-300">
              At Shree Ganesh Power Solutions, our mission is to empower homes and businesses with
              sustainable energy solutions. We are dedicated to providing high-quality solar
              installations that not only reduce energy costs but also contribute to a greener
              future.
            </p>
          </div>
          <div>
            <h2 class="text-2xl font-bold tracking-tight text-[var(--primary-color)]">
              Our Core Values
            </h2>
            <p class="mt-4 text-gray-300">
              Our core values revolve around integrity, innovation, and customer satisfaction. We
              believe in transparent communication, reliable service, and continuous improvement to
              meet the evolving needs of our clients.
            </p>
          </div>
        </div>
        <div class="space-y-8">
          <div>
            <h2 class="text-2xl font-bold tracking-tight text-[var(--primary-color)]">Our Story</h2>
            <p class="mt-4 text-gray-300">
              Founded in 2023, Shree Ganesh Power Solutions began with a vision to make solar energy
              accessible to everyone. Over the years, we have grown from a small startup to a
              leading solar installation company, serving a wide range of clients across
              residential, commercial, and industrial sectors.
            </p>
          </div>
          <div>
            <h2 class="text-2xl font-bold tracking-tight text-[var(--primary-color)]">
              Our Expertise
            </h2>
            <p class="mt-4 text-gray-300">
              Our team comprises experienced engineers, technicians, and project managers who are
              experts in solar technology. We stay updated with the latest advancements in the field
              to ensure our clients receive the most efficient and effective solutions.
            </p>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style type="text/tailwindcss">
:root {
  --primary-color: #38e07b;
}
.bg-gradient-radial {
  background-image: radial-gradient(circle at top, #1a3a24, #122118);
}
</style>
