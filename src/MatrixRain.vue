<script setup>
import { ref, onMounted } from 'vue'

const speed = defineProps({
  value: { type: Number, default: 1 } // 1 = normal, 0.5 = half speed
})

const canvasRef = ref(null)

onMounted(() => {
  const canvas = canvasRef.value
  const ctx = canvas.getContext('2d')

  canvas.width = window.innerWidth
  canvas.height = window.innerHeight

  const chars = '01{}<>;var'
  const fontSize = 18
  const columns = Math.floor(canvas.width / fontSize)

  // Base speed per column: slow but noticeable
  const drops = Array.from({ length: columns }, () => ({
    y: Math.random() * canvas.height,
    speed: (0.2 + Math.random() * 0.3) // 0.2 - 0.5
  }))

  function draw() {
    // Trail effect: subtle so code is visible
    ctx.fillStyle = 'rgba(0,0,0,0.05)'
    ctx.fillRect(0, 0, canvas.width, canvas.height)

    ctx.fillStyle = '#00ff00'
    ctx.font = fontSize + 'px monospace'

    for (let i = 0; i < drops.length; i++) {
      const drop = drops[i]
      const text = chars[Math.floor(Math.random() * chars.length)]
      ctx.fillText(text, i * fontSize, drop.y)

      drop.y += drop.speed * fontSize * speed.value

      if (drop.y > canvas.height) {
        drop.y = Math.random() * 50 // start slightly above for natural look
      }
    }

    requestAnimationFrame(draw)
  }

  draw()

  window.addEventListener('resize', () => {
    canvas.width = window.innerWidth
    canvas.height = window.innerHeight
  })
})
</script>

<template>
  <canvas ref="canvasRef" class="absolute inset-0 w-full h-full"></canvas>
</template>
