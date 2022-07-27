<template>
  <div>
    <h1>Hello How r u</h1>
    <h2>{{state.count}}</h2>
    <button @click="increment">
    <input type="text" placeholder="fname" v-model="mydata.fname">
    <input type="text" placeholder="add" v-model="mydata.add">
    <input type="number" placeholder="mobileno" v-model="mydata.mobileno">
    <p>My information is:{{mydata.fname + ' ' + mydata.add + ' ' +mydata.mobileno}}</p>
 click
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
    const mydata=reactive({
      fname:'vaibhav',
      add:'pune',
      mobileno:9876532234
    })

    // expose the state to the template
    return {
      state,
      increment,
      mydata
    }
  }

    
}
</script>

<style>

</style>