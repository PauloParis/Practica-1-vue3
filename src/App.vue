<script setup>
import { computed, ref } from 'vue';


const counter = ref (0);
const arrayCounter = ref([]);

const increment = () => counter.value ++;
const decrement = () => counter.value --;
const reset = () => counter.value = 0;
const add = () => {arrayCounter.value.push(counter.value)}

const classColorCounter = computed (() => {
  
  if(counter.value > 0) return 'positive'
  if(counter.value < 0) return 'negative'
  if(counter.value === 0) return 'zero'

}) 

const addDisabled = computed (() => {
  const findNumber = arrayCounter.value.find((num) => num === counter.value )
  if(findNumber || findNumber === 0) return true //return number || number === 0;
  else return false
})

</script>

<template>

  <div class="container text-center mt-5">
    <h2>Practica 1</h2>
    <h4 :class="classColorCounter">{{counter}}</h4>
    <div class="btn-group">
      <button @click="increment" class="btn btn-success">Increment</button>
      <button @click="decrement" class="btn btn-danger">Decrement</button>
      <button @click="reset" class="btn btn-secondary">Reset</button>
      <button @click="add" :disabled="addDisabled" class="btn btn-primary">Add</button>
  </div>
    <br> <br>
    <h3>Lista de números favoritos</h3>
    <ul class="list-group mt-4">
      <li class="list-group-item border border-0 bg-transparent text-white" v-for="(number, index) in arrayCounter" :key="index">
        {{arrayCounter[index]}}  
      </li>
    </ul>
  </div>
  
</template>

<style>

.positive {
  color: green;
}
.negative {
  color: red;
}
.zero {
  color: blue;
}

</style>
