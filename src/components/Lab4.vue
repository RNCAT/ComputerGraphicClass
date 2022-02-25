<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title">Lab4: Arc</p>
    </header>
    <div class="card-content">
      <div class="content">
        <canvas id="lab4" width="320" height="200"></canvas>
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
      colors: [['#406882', '#6998AB', '#B1D0E0'], ['#146356', '#A3DA8D', '#F3C892'], ['#121212', '#30475E', '#F05454']],
      x: 60,
      y: 100,
      radius: 50,
      startAng: Math.PI,
      stopAng: 2 * Math.PI
    }
  },
  methods: {
    createArc(x, y, color, lineWidth) {
      this.ctx.beginPath()
      this.ctx.arc(x, y, this.radius, this.startAng, this.stopAng)
      this.ctx.strokeStyle = color
      this.ctx.lineWidth = lineWidth
      this.ctx.stroke()
      this.ctx.closePath()
    },
  },
  mounted() {
    this.canvas = document.getElementById('lab4')
    this.ctx = this.canvas.getContext('2d')

    for (let i = 0, j = 0; i < 300; i += 100, j++) {
      this.createArc(this.x + i, this.y, this.colors[j][0], 6)
      this.createArc(this.x + i, this.y + 4, this.colors[j][1], 5)
      this.createArc(this.x + i, this.y + 8, this.colors[j][2], 4)
    }
  }
}
</script>