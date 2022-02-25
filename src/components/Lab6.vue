<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title">Lab6: BezierCurve</p>
    </header>
    <div class="card-content">
      <div class="content">
        <canvas id="lab6" width="150" height="200"></canvas>
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
    writeHeart(color) {
      this.ctx.beginPath();
      this.ctx.moveTo(100, 100);
      this.ctx.bezierCurveTo(100, 37, 70, 25, 50, 25);
      this.ctx.bezierCurveTo(30, 25, 30, 60, 30, 60);
      this.ctx.bezierCurveTo(30, 80, 50, 102, 80, 120);
      this.ctx.bezierCurveTo(110, 102, 130, 80, 130, 60);
      this.ctx.bezierCurveTo(130, 60, 130, 25, 100, 25);
      this.ctx.bezierCurveTo(85, 25, 80, 37, 80, 50);
      this.ctx.fillStyle = color
      this.ctx.fill();
      this.ctx.closePath()
    }
  },
  mounted() {
    this.canvas = document.getElementById('lab6')
    this.ctx = this.canvas.getContext('2d')

    this.writeHeart('#ff4500')
  }
}
</script>