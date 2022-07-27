<template>
  <div>
    <h1>Hello How r u</h1>
    <h2>{{ state.count }}</h2>
    <button @click="increment">click</button> <br><br>
    <input type="text" placeholder="fname" v-model="mydata.fname" />
    <input type="text" placeholder="add" v-model="mydata.add" />
    <input type="number" placeholder="mobileno" v-model="mydata.mobileno" />
    <input type="color" v-model="state.mycolor"/><br><br>
    <button @click="state.show = !state.show">{{state.show ? 'Hide' : 'show'}}</button><br>
    
    <p v-if="state.show" :style="{color: state.mycolor}" id="myname">My information is:- {{ mydata.info }}</p>
    <p v-else :style="{color: state.mycolor}">Data Not Displayed Yet</p><br><br>
      <button @click="ChangeColor()">change color</button>
    <p v-for="item of state.mylist"> Name:{{item.Name}} And age is{{item.age}}
    </p>
    
    <button @click="add" id="object" >Add Object Data</button><br><br>
  

  </div>

</template>

<script>
import { reactive } from "vue";

// const state = reactive({ count: 0 });
export default {
  setup() {
    const state = reactive({count: 0,
    show:false,
    mylist:[
      {Name:'Vaibhav', age:22},
      {Name:'Akash', age: 21},
      {Name:'Nitin', age:24}
      ]
    });
//for information change color
    function ChangeColor() {
      document.getElementById("myname").style.color = "#FF0000";
    }
// for added data into object 
    function add(){
      state.mylist.push({Name:"Rahul", age:13})
    }

// for using count function

    function increment() {
      state.count++;
    }
    
  // reactive method using this method we can add object and array also
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
      ChangeColor,
      add
    };
  },
};
</script>

<style></style>
