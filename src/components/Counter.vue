<script setup>
import { ref } from 'vue'
import CounterButton from './atoms/MainButton.vue'

const count = ref(0)

const increment = () => {
  count.value++
}

const decrement = () => {
  if (count.value > 0) {
    count.value--
  }
}

const reset = () => {
  count.value = 0
}
</script>

<template>
  <div class="wrap">
    <div>
      <h1>Counter App</h1>

      <div class="btn-wrap">
        <CounterButton @click="decrement">-</CounterButton>
        <p>{{ count }}</p>
        <CounterButton @click="increment">+</CounterButton>
      </div>

      <CounterButton @click="reset">Reset</CounterButton>
    </div>
  </div>
</template>

<style scoped>
.wrap {
  display: flex;
  justify-content: center;
}
.wrap > div {
  display: block;
  text-align: center;
  width: 100%;
  max-width: 720px;
  box-shadow: 0 0 4px #000;
  height: 100vh;
  padding: 2rem;
}
h1 {
  margin-bottom: 3rem;
}
.btn-wrap {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-bottom: 2rem;
}

p {
  margin: 0;
}
</style>
