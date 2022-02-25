<script setup>
import Lab1 from './components/Lab1.vue'
import Lab2 from './components/Lab2.vue'
import Lab3 from './components/Lab3.vue'
import Lab4 from './components/Lab4.vue'
import Lab5 from './components/Lab5.vue'
import Lab6 from './components/Lab6.vue'
import Lab7 from './components/Lab7.vue'
import Lab8 from './components/Lab8.vue'
import Lab9 from './components/Lab9.vue'
import Midterm from './components/Midterm.vue'
import Footer from './components/Footer.vue'
</script>

<template>
  <div class="container">
    <div class="columns">
      <div class="column">
        <Lab1 />
      </div>
      <div class="column">
        <Lab2 />
      </div>
      <div class="column">
        <Lab3 />
      </div>
      <div class="column">
        <Lab4 />
      </div>
    </div>

    <div class="columns">
      <div class="column">
        <Lab5 />
      </div>
      <div class="column">
        <Lab6 />
      </div>
      <div class="column">
        <Lab7 />
      </div>
      <div class="column">
        <Lab8 />
      </div>
    </div>
    <div class="columns">
      <div class="column"></div>
      <div class="column">
        <Lab9 />
      </div>
      <div class="column">
        <Midterm />
      </div>
      <div class="column"></div>
    </div>
  </div>
  <Footer />
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Kanit:wght@400;500;700&display=swap");

#app {
  font-family: "Kanit", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
