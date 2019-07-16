<template>
<div id="app">
  <h2>Counter</h2>
  <h2>{{ count }}</h2>
  <input type="number" v-model="entry" />
  <div class="div__buttons">
    <button class="incrementButton" @click.prevent="handleIncrement">
      Increment
    </button>
    <button class="decrementButton" @click.prevent="handleDecrement">
      Decrement
    </button>
  </div>
  <p>{{ text }}</p>
</div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'app',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
