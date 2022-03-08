<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title">Lab11: Clock</p>
    </header>
    <div class="card-content">
      <div class="content">
        <canvas id="Nairobi" width="300" height="300"></canvas>
        <canvas id="Tokyo" width="300" height="300"></canvas>
        <canvas id="London" width="300" height="300"></canvas>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      radius: 120
    }
  },
  methods: {
    drawClock(ctx, radius, timeZoneOffset) {
      this.drawFace(ctx, radius)
      this.drawNumbers(ctx, radius)
      this.drawTime(ctx, radius, timeZoneOffset)
      this.drawText(ctx)
    },

    drawText(ctx) {
      ctx.font = '30px roboto'
      ctx.textAlign = 'center'
      ctx.fillStyle = '#3f3f3f'
      ctx.fillText(ctx.canvas.id, 0, 150)
    },

    drawFace(ctx, radius) {
      ctx.beginPath()
      ctx.arc(0, 0, radius, 0, 2 * Math.PI)
      ctx.fillStyle = '#ffffff'
      ctx.fill()
      ctx.strokeStyle = '#333333'
      ctx.lineWidth = radius * 0.1
      ctx.stroke()
      ctx.beginPath()
      ctx.arc(0, 0, radius * 0.05, 0, 2 * Math.PI)
      ctx.fillStyle = '#cccccc'
      ctx.fill()
    },

    drawNumbers(ctx, radius) {
      ctx.font = radius * 0.15 + 'px roboto'
      ctx.textBaseline = 'middle'
      ctx.textAlign = 'center'
      ctx.fillStyle = '#3f3f3f'
      for (let num = 1; num < 13; num++) {
        let angle = (num * Math.PI) / 6
        ctx.rotate(angle)
        ctx.translate(0, -radius * 0.85)
        ctx.rotate(-angle)
        ctx.fillText(num.toString(), 0, 0)
        ctx.rotate(angle)
        ctx.translate(0, radius * 0.85)
        ctx.rotate(-angle)
      }
    },

    drawTime(ctx, radius, timeZoneOffset) {
      const now = new Date()
      const UTC = now.getTime() + now.getTimezoneOffset() * 60000
      const UTCTime = new Date(UTC + 3600000 * timeZoneOffset)
      let hour = UTCTime.getHours()
      let minute = UTCTime.getMinutes()
      let second = UTCTime.getSeconds()

      hour = hour % 12
      hour = (hour * Math.PI) / 6 + (minute * Math.PI) / (6 * 60) + (second * Math.PI) / (360 * 60)
      this.drawHand(ctx, hour, radius * 0.5, radius * 0.07)

      minute = (minute * Math.PI) / 30 + (second * Math.PI) / (30 * 60)
      this.drawHand(ctx, minute, radius * 0.8, radius * 0.07)

      second = (second * Math.PI) / 30
      this.drawHand(ctx, second, radius * 0.9, radius * 0.02)
    },

    drawHand(ctx, pos, length, width) {
      ctx.beginPath()
      ctx.lineWidth = width
      ctx.lineCap = 'round'
      ctx.moveTo(0, 0)
      ctx.rotate(pos)
      ctx.lineTo(0, -length)
      ctx.stroke()
      ctx.rotate(-pos)
    }
  },
  mounted() {
    const cvNairobi = document.getElementById('Nairobi')
    const ctxNairobi = cvNairobi.getContext('2d')
    const cvTokyo = document.getElementById('Tokyo')
    const ctxTokyo = cvTokyo.getContext('2d')
    const cvLondon = document.getElementById('London')
    const ctxLondon = cvLondon.getContext('2d')

    ctxNairobi.translate(this.radius, this.radius)
    ctxTokyo.translate(this.radius, this.radius)
    ctxLondon.translate(this.radius, this.radius)
    this.radius = this.radius * 0.9

    setInterval(() => {
      this.drawClock(ctxNairobi, this.radius, 2)
      this.drawClock(ctxTokyo, this.radius, 9)
      this.drawClock(ctxLondon, this.radius, 0)
    }, 1000)
  }
}
</script>

<style scoped>
canvas {
  margin-right: 5px;
}
</style>