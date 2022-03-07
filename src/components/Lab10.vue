<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title">Lab10: TrafficLight</p>
    </header>
    <div class="card-content">
      <div class="content">
        <canvas id="ch1" width="160" height="320"></canvas>
        <canvas id="ch2" width="160" height="320"></canvas>
        <canvas id="ch3" width="160" height="320"></canvas>
        <canvas id="ch4" width="160" height="320"></canvas>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      defaultColor: '#000000',
      lightRadius: 30,
      lights: [
        { x: 80, y: 80, color: '#ff0404' },
        { x: 80, y: 160, color: '#0eff00' },
        { x: 80, y: 240, color: '#ffd500' },
      ],
      channels: [
        {
          id: 'ch1',
          queue: [
            { index: 0, time: 10000 },
            { index: 1, time: 10000 },
            { index: 2, time: 5000 },
          ],
        },
        {
          id: 'ch2',
          queue: [
            { index: 1, time: 10000 },
            { index: 2, time: 5000 },
            { index: 0, time: 10000 },
          ],
        },
        {
          id: 'ch3',
          queue: [
            { index: 2, time: 5000 },
            { index: 0, time: 10000 },
            { index: 1, time: 10000 },
          ],
        },
        {
          id: 'ch4',
          queue: [
            { index: 0, time: 10000 },
            { index: 1, time: 10000 },
            { index: 2, time: 5000 },
          ],
        },
      ]
    }
  },
  methods: {
    createLight(ctx, lights) {
      lights.forEach((light) => {
        ctx.beginPath()

        ctx.arc(light.x, light.y, this.lightRadius, 0, 2 * Math.PI, false)
        ctx.strokeStyle = this.defaultColor
        ctx.fillStyle = this.defaultColor
        ctx.stroke()
        ctx.fill()
      })
    },


    turnOn(ctx, light) {
      ctx.beginPath()
      ctx.arc(light.x, light.y, this.lightRadius, 0, 2 * Math.PI, false)
      ctx.strokeStyle = light.color
      ctx.fillStyle = light.color
      ctx.stroke()
      ctx.fill()
    },

    turnOff(ctx, light) {
      ctx.beginPath()
      ctx.arc(light.x, light.y, this.lightRadius, 0, 2 * Math.PI, false)
      ctx.strokeStyle = this.defaultColor
      ctx.fillStyle = this.defaultColor
      ctx.stroke()
      ctx.fill()
    },

    run(ctx, queue) {
      this.turnOn(ctx, this.lights[queue[0].index])

      setTimeout(() => {
        this.turnOff(ctx, this.lights[queue[0].index])
        this.turnOn(ctx, this.lights[queue[1].index])

        setTimeout(() => {
          this.turnOff(ctx, this.lights[queue[1].index])
          this.turnOn(ctx, this.lights[queue[2].index])

          setTimeout(() => {
            this.turnOff(ctx, this.lights[queue[2].index])
          }, queue[2].time)
        }, queue[1].time)
      }, queue[0].time)
    },

    traffic() {
      this.channels.forEach((channel, index) => {
        const canvas = document.getElementById(channel.id)
        const ctx = canvas.getContext('2d')

        this.createLight(ctx, this.lights)
        this.run(ctx, channel.queue)
      })
    }
  },
  async mounted() {
    await this.traffic(this.channels)

    setInterval(async () => {
      await this.traffic(this.channels)
    }, 25000)
  }
}
</script>

<style scoped>
canvas {
  border: 2px solid black;
  margin-right: 5px;
}
</style>