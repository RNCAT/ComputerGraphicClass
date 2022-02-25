<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title">Lab9: Graph</p>
    </header>
    <div class="card-content">
      <div class="content">
        <canvas id="lab9" width="300" height="300"></canvas>
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
      bars: [
        [100, 250, 100, 30, "#EEE6CE"],
        [130, 250, 130, 60, "#2EB086"],
        [160, 250, 160, 90, "#B8405E"],
        [190, 250, 190, 150, "#313552"],
      ]
    }
  },
  methods: {
    barGraph(bars) {
      bars.forEach(bar => {
        this.ctx.beginPath()
        this.ctx.moveTo(bar[0], bar[1])
        this.ctx.lineTo(bar[2], bar[3])
        this.ctx.lineWidth = 20
        this.ctx.strokeStyle = bar[4]
        this.ctx.stroke()
        this.ctx.closePath()
      });
    },

    xyLine(x1, y1, x2, y2) {
      this.ctx.beginPath()
      this.ctx.moveTo(x1, y1)
      this.ctx.lineTo(x2, y2)
      this.ctx.strokeStyle = "#000000"
      this.ctx.lineWidth = 2
      this.ctx.stroke()
      this.ctx.closePath()
    },

    head(x, y) {
      this.ctx.font = '18px Roboto'
      this.ctx.fillText('กราฟแท่ง', x, y)
    }
  },
  mounted() {
    this.canvas = document.getElementById('lab9')
    this.ctx = this.canvas.getContext('2d')

    this.barGraph(this.bars)
    this.xyLine(50, 250, 300, 250)
    this.xyLine(50, 250, 50, 10)
    this.head(100, 280)
  }
}
</script>