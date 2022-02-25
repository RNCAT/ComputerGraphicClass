<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title">Lab8: Pattern</p>
    </header>
    <div class="card-content">
      <div class="content">
        <canvas id="lab8" width="300" height="200"></canvas>
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
      imageURL: 'http://placekitten.com/100/100'
    }
  },
  methods: {
    createPattern(patternStyle) {
      let img = new Image()
      img.src = this.imageURL

      img.onload = () => {
        const pattern = this.ctx.createPattern(img, patternStyle)
        this.ctx.fillStyle = pattern
        this.ctx.fillRect(0, 0, this.canvas.width, this.canvas.height)
      }
    }
  },
  mounted() {
    this.canvas = document.getElementById('lab8')
    this.ctx = this.canvas.getContext('2d')

    this.createPattern('repeat')
  }
}
</script>