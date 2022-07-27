<template>
  <div>
    <input v-model="firstname.fname">
    <h1>{{firstname.fname}}</h1>
    <h1>Hello How Are you...!</h1>
    <h2>{{state.count}}</h2>
    <button @click="increment">
 click
</button>
  </div>
</template>


<script>
import { ref } from 'vue'


import { reactive } from 'vue'
let firstname=ref({ fname:null})

const state = reactive({ count: 0 })
export default {
     setup() {
    const state = reactive({ count: 0 })
      function increment() {
      state.count++
    
     books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
  
      }
      

    
    return {
      state,
      increment,
      firstname
    }
  }

    
}
</script>



<style>

</style>