<template>
  <div>
    <h1>Hello How r u</h1>
    <h2>{{ state.count }}</h2>
    <button @click="increment">click</button>
    <input type="text" placeholder="fname" v-model="mydata.fname" />
    <input type="text" placeholder="add" v-model="mydata.add" />
    <input type="number" placeholder="mobileno" v-model="mydata.mobileno" />
    <input type="color" v-model="state.mycolor"/>
    <p :style="{color: state.mycolor}" id="myname">My information is:{{ mydata.info }}</p>
    <button @click="ChangeColor()">change color</button>

  </div>
</template>

<script>
import { reactive } from "vue";

// const state = reactive({ count: 0 });
export default {
  setup() {
    const state = reactive({count: 0});

    function ChangeColor() {
      document.getElementById("myname").style.color = "#FF0000";
    }



    function increment() {
      state.count++;
    }
    const mydata = reactive({
      mycolor:'#00ff00',
      fname: "vaibhav",
      add: "pune",
      mobileno: 9876532234,
      info: computed(() => {
        return (
          mydata.fname +
          " " +
          mydata.add +
          " " +
          mydata.mobileno +
          " " +
          "Sambhajinagar"
        );
      }),
    });

    // expose the state to the template
    return {
      state,
      increment,
      mydata,
      ChangeColor
    };
  },
};
</script>

<style></style>
