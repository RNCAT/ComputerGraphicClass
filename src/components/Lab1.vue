<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title">Lab 1: Pixel & Rectangle</p>
    </header>
    <div class="card-content">
      <div class="content">
        <canvas id="lab1" width="250" height="200"></canvas>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    drawFlag() {
      const canvas = document.getElementById('lab1')
      const ctx = canvas.getContext('2d')

      ctx.fillStyle = '#A51931'
      ctx.fillRect(0, 0, 250, 30)

      ctx.fillStyle = '#F4F5F8'
      ctx.fillRect(0, 30, 250, 30)

      ctx.fillStyle = '#2D2A4A'
      ctx.fillRect(0, 60, 250, 50)

      ctx.fillStyle = '#F4F5F8'
      ctx.fillRect(0, 110, 250, 30)

      ctx.fillStyle = '#A51931'
      ctx.fillRect(0, 140, 250, 30)
    }
  },
  mounted() {
    this.drawFlag()
  }
}
</script>

