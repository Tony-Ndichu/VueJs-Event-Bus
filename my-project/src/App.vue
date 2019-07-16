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
import EventBus from './components/helpers/eventBus';

export default {
    el: '#app',
    data() {
      return {
        count: 0,
        text: '',
        entry: 0
      }
    },
    created() {
      EventBus.$on('count-incremented', (count) => {
        this.text = `Count was increased by ${count}`
        setTimeout(() => {
          this.text = '';
        }, 3000);
      })
      EventBus.$on('count-decremented', () => {
        this.text = `Count was decreased`
        setTimeout(() => {
          this.text = '';
        }, 3000);
      })
    },
    methods: {
      handleIncrement() {
        this.count += parseInt(this.entry, 10);
        EventBus.$emit('count-incremented', this.entry)
        this.entry = 0;
      },
      handleDecrement() {
        this.count -= parseInt(this.entry, 10);
        EventBus.$emit('count-decremented')
        this.entry = 0;
      }
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
