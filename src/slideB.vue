<script setup>
import GradientParticles from './GradientParticles.vue'
</script>

<template>
  <div class="relative hero min-h-screen overflow-hidden bg-base-200">
    <!-- Background particles and gradient -->
    <GradientParticles />

    <!-- Foreground content -->
    <div class="relative z-10 hero-content flex-col lg:flex-row-reverse">
      <img
        src="https://img.daisyui.com/images/stock/photo-1635805737707-575885ab0820.webp"
        class="max-w-sm rounded-lg shadow-2xl"
      />
      <div>
        <h1 class="text-5xl font-bold">welcome to codemitra</h1>
        <p class="py-6">
          Hey everyone! CodeMitra is our college’s very own coding society, started just last year, and it’s all about bringing together students who love to tinker with code, solve challenges, and create cool projects.

          Whether it’s casual coding sessions over coffee, friendly hackathons, mini competitions, fun tech talks, or just sharing tips and tricks, CodeMitra is the place to explore, learn, and have fun with tech.

          Come join us, meet fellow coders, and let’s make coding a little less intimidating and a lot more exciting!
        </p>
        <button class="btn btn-primary">join now</button>
      </div>
    </div>
  </div>
</template>
