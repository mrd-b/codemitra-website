<script setup>
import { ref, onMounted } from 'vue'
import slideA from './slideA.vue'
import slidenav from './slidenav.vue'
import slideB from './slideB.vue'
import slidefoot from './slidefoot.vue'

const showSlideA = ref(false)
const showSlideB = ref(false)

onMounted(() => {
  // Animate SlideA after small delay
  setTimeout(() => {
    showSlideA.value = true
  }, 300)

  // Animate SlideB on scroll
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          showSlideB.value = true
        }
      })
    },
    { threshold: 0.2 }
  )

  const target = document.querySelector('#slideB-section')
  if (target) observer.observe(target)
})
</script>

<template>
  <div>
    <!-- Navigation -->
    <slidenav />

    <!-- Slide A (with entry animation) -->
    <div
      :class="[
        'transition-all duration-1000 ease-[cubic-bezier(0.22,1,0.36,1)]',
        showSlideA 
          ? 'opacity-100 scale-100 translate-y-0'
          : 'opacity-0 scale-50 -translate-y-10'
      ]"
    >
      <slideA />
    </div>

    <!-- Slide B (scroll animation) -->
    <div
      id="slideB-section"
      :class="[
        'transition-all duration-1000 ease-[cubic-bezier(0.22,1,0.36,1)]',
        showSlideB 
          ? 'opacity-100 scale-100 translate-y-0 rotate-0'
          : 'opacity-0 scale-75 translate-y-10 rotate-3'
      ]"
    >
      <slideB />
    </div>
    <!-- Footer -->
    <slidefoot />
  </div>
</template>
