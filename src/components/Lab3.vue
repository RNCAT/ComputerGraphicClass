<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title">Lab3: Circle</p>
    </header>
    <div class="card-content">
      <div class="content">
        <canvas id="lab3" width="200" height="200"></canvas>
      </div>
    </div>
  </div>
</template>

<script>


export default {
  methods: {
    createCircle(ctx, x, y, color) {
      const startAng = 0
      const stopAng = 2 * Math.PI
      const radius = 50

      ctx.beginPath()
      ctx.arc(x, y, radius, startAng, stopAng)
      ctx.fillStyle = color
      ctx.fill()
      ctx.closePath()
    },
  },
  mounted() {
    const canvas = document.getElementById('lab3')
    const ctx = canvas.getContext('2d')

    const halfWidth = (canvas.width / 2) - 25
    const treeHeight = canvas.height / 3

    const colors = ['#EA2552', '#1E8755', '#2C2C6A']

    for (let i = 0, wStart = 0; i < 3; i++, wStart += 25) {
      const x = halfWidth + wStart
      const y = i % 2 ? treeHeight + 50 : treeHeight
      this.createCircle(ctx, x, y, colors[i])
    }
  }
}
</script>