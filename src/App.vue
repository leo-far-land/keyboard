<template>
  <div id="app">
    <p class="font-weight-bold" style="font-size: 24pt;">Keyboard Vue</p>
    <img src="./assets/logo.png" alt="">
    <app-textarea :text="text" ></app-textarea>
    <app-keyboard @text="text = $event"></app-keyboard>
  </div>
</template>

<script>
import AppKeyboard from './components/AppKeyboard.vue'
import AppTextarea from './components/AppTextarea.vue'

export default {
  name: 'App',
  data() {
    return {
      text: "",
    }
  },
  components: {
    AppTextarea, 
    AppKeyboard
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
