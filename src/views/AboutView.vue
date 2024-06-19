<template>
  <div>
<!-- v-on or @click used as Event listener to the counter  -->
    <h1>Counter -> <span>{{counter}}</span> </h1>
    <div><button @click="increment()">Increment</button>
    <button @click="decrement()">Decrement</button></div>
    <!-- Attach javascript value to an attribute tag  -->
    <img v-bind:src="imgUrl">
  </div>
    

  <div>

    <!-- Class binding  -->
  <h4 :class="{hello:check}">Conditional rendering </h4> 
  
  <!-- Conditional binding  -->
<h1 v-if="check">The value is true </h1>

<h1 v-else>The value is false </h1>
<button @click ="checkCondition()">Change state</button>
<h1 v-show="check">This contains the v-show </h1>


<ul>
<!-- <li v-for="sport,index in sports" :key="index">{{ sport }}</li> -->
<li v-for="({message},index) in objects" :key="index">{{message }}</li>
</ul>
<!-- One way Binding  -->
<h3>{{oneWayText}}</h3>
<!-- 2 way data binding  -->
<h3>{{twoWayText}}</h3>
<input type="text" v-model="twoWayText">
  </div>
  <info-comp first-name="hehe" last-name="hehhehhehhe"/>
  <!-- <info-comp first-name="hehe1"/>


  v-bind : -->
  <info-comp :object-data="singleObject"/>

  <info-comp>
Hehe I am using slots
  </info-comp>

<slot-comp>
  <template #slotTitle>
Card Slot
  </template>
  <template #default>
<img :src="imgUrl">
  </template>
</slot-comp>


</template>
<script>

import infoComp from '../components/infoComp.vue'
import SlotComp from '../components/SlotComp.vue'

export default {
 data(){
  return{
      counter:0 ,
      imgUrl:'data:image/jpeg;base64,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',
  check: true ,
  sports:['soccer','netball','voleyball'],
   
    objects: [
      {message:'Hello There 1',id:1},
      {message:'Hello There 2',id:2},
      {message:'Hello There 3',id:3}
    ],
    singleObject:{
      name:'Matt',
      surname:'Brown'

    },
    oneWayText:'hehe',
    twoWayText:'hehe 2.0'
 }
 
 
 } ,
 components:{
  infoComp,
  SlotComp,
  
 },

 methods:{
  increment(){
      this.counter ++
  },
  decrement(){
      this.counter --
  },
  checkCondition(){
    this.check =!this.check

  }
 }
}
</script>
<style scoped >
  h1{
      color:blue
  }
  h4{
    color: orangered;
  }
</style>