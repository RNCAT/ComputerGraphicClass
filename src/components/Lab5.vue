<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title">Lab5: quadraticCurve</p>
    </header>
    <div class="card-content">
      <div class="content">
        <canvas id="lab5" width="200" height="200"></canvas>
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
    }
  },
  methods: {
    writeText(text, size, x, y) {
      const gradient = this.ctx.createLinearGradient(0, 0, this.canvas.width, 0)
      gradient.addColorStop("0", "magenta")
      gradient.addColorStop("0.5", "blue")
      gradient.addColorStop("1.0", "red")

      this.ctx.font = `${size}px Verdana`
      this.ctx.fillStyle = gradient
      this.ctx.fillText(text, x, y)
    },

    writeMsgBox() {
      this.ctx.beginPath()
      this.ctx.moveTo(100, 50)
      this.ctx.quadraticCurveTo(50, 40, 50, 80)
      this.ctx.quadraticCurveTo(50, 100, 75, 100)
      this.ctx.quadraticCurveTo(65, 115, 50, 120)
      this.ctx.quadraticCurveTo(75, 115, 85, 100)
      this.ctx.quadraticCurveTo(120, 100, 120, 80)
      this.ctx.quadraticCurveTo(120, 50, 100, 50)
      this.ctx.lineWidth = 2
      this.ctx.stroke()
      this.ctx.closePath()
    }
  },
  mounted() {
    this.canvas = document.getElementById('lab5')
    this.ctx = this.canvas.getContext('2d')

    this.writeMsgBox()
    this.writeText('Jaruwat', 12, 60, 70)
    this.writeText('Thongchana', 10, 55, 85)
  }
}
</script>