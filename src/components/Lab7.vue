<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title">Lab7: Colors</p>
    </header>
    <div class="card-content">
      <div class="content">
        <canvas id="lab7" width="150" height="200"></canvas>
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

      startAng: 0,
      stopAng: 2 * Math.PI,
      radius: 50,
      colors: ['#EA2552', '#1E8755', '#2C2C6A']
    }
  },
  methods: {
    createCircle(x, y, color) {
      this.ctx.beginPath()
      this.ctx.arc(x, y, this.radius, this.startAng, this.stopAng)
      this.ctx.globalCompositeOperation = "lighter"
      this.ctx.fillStyle = color
      this.ctx.fill()
      this.ctx.closePath()
    }
  },
  mounted() {
    this.canvas = document.getElementById('lab7')
    this.ctx = this.canvas.getContext('2d')

    const halfWidth = (this.canvas.width / 2) - 25
    const treeHeight = this.canvas.height / 3

    for (let i = 0, wStart = 0; i < 3; i++, wStart += 25) {
      const x = halfWidth + wStart
      const y = i % 2 ? treeHeight + 50 : treeHeight
      this.createCircle(x, y, this.colors[i])
    }
  }
}
</script>