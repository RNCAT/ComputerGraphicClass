<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title">Lab2: Line</p>
    </header>
    <div class="card-content">
      <div class="content">
        <canvas id="lab2" width="300" height="200"></canvas>
      </div>
    </div>
  </div>
</template>

<script>


export default {
  methods: {
    drawLine() {
      const canvas = document.getElementById('lab2')
      const ctx = canvas.getContext('2d')

      ctx.beginPath()
      ctx.moveTo(canvas.width / 2, 0)
      ctx.lineTo(canvas.width / 2, canvas.height)
      ctx.lineWidth = 4
      ctx.strokeStyle = '#ffffff'
      ctx.lineCap = 'round'
      ctx.stroke()

      ctx.beginPath()
      ctx.moveTo(0, canvas.height / 2)
      ctx.lineTo(canvas.width, canvas.height / 2)
      ctx.lineWidth = 4
      ctx.strokeStyle = '#ffffff'
      ctx.lineCap = 'round'
      ctx.stroke()
    }
  },
  mounted() {
    this.drawLine()
  }
}
</script>

<style scoped>
#lab2 {
  background-image: url("http://placekitten.com/300/200");
}
</style>