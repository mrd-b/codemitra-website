<script setup lang="ts">
import RotatingText from './TextAnimations/RotatingText.vue'
import GradientParticles from './GradientParticles.vue'
</script>

<template>
  <div class="relative h-screen flex items-center justify-center overflow-hidden bg-gray-900 text-white text-4xl font-bold">
    <!-- Background particles and gradient -->
    <GradientParticles />

    <!-- Foreground content -->
    <div class="relative z-10 flex items-center">
      <span class="mr-3">Join Codemitra for:</span>
      <RotatingText
        :texts="['Peers', 'DSA', 'Hackathons', 'Projects', 'Fun!']"
        mainClassName="px-4 bg-green-300 text-black overflow-hidden py-2 rounded-lg"
        staggerFrom="last"
        :initial="{ y: '100%' }"
        :animate="{ y: 0 }"
        :exit="{ y: '-120%' }"
        :staggerDuration="0.05"
        splitLevelClassName="overflow-hidden pb-1"
        :transition="{ type: 'spring', damping: 30, stiffness: 400 }"
        :rotationInterval="2000"
      />
    </div>
  </div>
</template>
