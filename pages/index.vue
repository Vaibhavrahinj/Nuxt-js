<template>
  <div>
    <h1>Hello How r u</h1>
    <h2>{{state.count}}</h2>
    <button @click="increment">
  {{ state.count }}
</button>
  </div>
</template>

<script>
import { reactive } from 'vue'

const state = reactive({ count: 0 })
export default {
     setup() {
    const state = reactive({ count: 0 })
      function increment() {
      state.count++
    }

    // expose the state to the template
    return {
      state,
      increment
    }
  }

    
}
</script>

<style>

</style>