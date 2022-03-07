<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title">Midterm: Like</p>
    </header>
    <div class="card-content">
      <div class="content">
        <canvas id="midterm" width="180" height="300"></canvas>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      canvas: null,
      ctx: null,
      likes: [
        [50, 50, 100, 50],
        [100, 50, 95, 30],
        [110, 30, 115, 50],
        [140, 50, 145, 50],
        [155, 55, 145, 90],
        [145, 90, 50, 90],
        [50, 90, 50, 50],
      ]
    }
  },
  methods: {
    drawLike() {
      this.ctx.beginPath()
      this.ctx.moveTo(50, 50)
      this.likes.forEach(elements => {
        this.ctx.quadraticCurveTo(...elements)
      })
      this.ctx.lineWidth = 3
      this.ctx.stroke()
      this.ctx.closePath()

      this.ctx.beginPath()
      this.ctx.moveTo(70, 50)
      this.ctx.quadraticCurveTo(70, 50, 70, 90)
      this.ctx.lineWidth = 3
      this.ctx.stroke()
      this.ctx.closePath()
    }

  },
  mounted() {
    this.canvas = document.getElementById('midterm')
    this.ctx = this.canvas.getContext('2d')

    this.drawLike()
  }
}
</script>