<template>
  <div>
    <NuxtLink to="/">Demo Page</NuxtLink>
    <h1>Hello How Are you ...!</h1>
    <h2>{{ state.count }}</h2>
    <button  class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded" @click="increment">Count</button> <br><br>
    <input type="text" placeholder="fname" v-model="mydata.fname" />
    <input type="text"  class="px-4 py-3" placeholder="add" v-model="mydata.add" />
    <input type="number" placeholder="mobileno" v-model="mydata.mobileno" />
    <input type="color" v-model="state.mycolor"/><br><br>
    <button  class="bg-red-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded" @click="state.show = !state.show">{{state.show ? 'Hide' : 'show'}}</button><br>
    
    <p v-if="state.show" :style="{color: state.mycolor}" id="myname">My information is:- {{ mydata.info }}</p>
    <p v-else :style="{color: state.mycolor}">Data Not Displayed Yet</p><br><br>
      <button  class="bg-green-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded" @click="ChangeColor()">change color</button>
    <p v-for="item of state.mylist"> Name: {{item.Name}} And age is {{item.age}}
    </p>
    
    <button class="bg-green-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded" @click="add" id="object" >Add Object Data</button><br><br>
  
<Demo></Demo>
<Contact></Contact>
  </div>
  
</template>

<script>
import DemoComp from '~/component/Demo.vue'
import ContactPage from '~/pages/_contact.vue'
definePageMeta({
  components:{
    DemoComp,
    ContactPage,
  }
})
import { reactive } from "vue";
import Demo from "../component/Demo.vue";
import _contact from './_contact.vue';

// const state = reactive({ count: 0 });
export default {
    setup() {
        const state = reactive({ count: 0, show: true, mylist: [
                { Name: "Madhuri", age: 23 },
                { Name: "Komal", age: 23 },
                { Name: "Shubhangi", age: 23 }
            ]
        });
        //for information change color
        function ChangeColor() {
            document.getElementById("myname").style.color = "#FF0000";
        }
        // for added data into object 
        function add() {
            state.mylist.push({ Name: "Rahul", age: 13 });
        }
        //  Wachers
        onMounted(() => {
            console.log("My component has been mounted");
        });
        watch(state, (newvalue, oldvalue) => {
            console.log(newvalue);
        });
        // for using count function
        function increment() {
            state.count++;
        }
        // reactive method using this method we can add object and array also
        const mydata = reactive({
            mycolor: "rgb(222,130,202)",
            fname: "Madhuri",
            add: "pune",
            mobileno: 9322240107,
            info: computed(() => {
                return (mydata.fname +
                    " " +
                    mydata.add +
                    " " +
                    mydata.mobileno +
                    " " +
                    "Ahamadnagar");
            }),
        });
        // expose the state to the template
        return {
            state,
            increment,
            mydata,
            ChangeColor,
            add,
            watch,
            onMounted
        };
    },
    components: { Demo, _contact }
};
</script>

<style>

</style>
