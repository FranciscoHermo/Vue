<script setup>
import {computed, ref} from 'vue'
const name = 'Vue dinamico'
const counter = ref(0)

const arrayFavoritos = ref([])

const increment = () => {
  counter.value ++;
}
const decrement = () => {
  counter.value --;
}
const Reset = () => {
  counter.value = 0;
}

const add = () => {
  arrayFavoritos.value.push(counter.value)
}

const blockBtnAdd = computed(() => {
  const numSearch = arrayFavoritos.value.find(num => num === counter.value)
  console.log(numSearch);
  // if(numSearch === 0) return true;
  // return numSearch ? true : false;
  return numSearch || numSearch === 0
})
</script>

<template>
  <div class="countainer text-center mt-3">
    <h1>Hola {{ name.toUpperCase()}}</h1>  
    <h2 :class="counter > 0 ? 'positive' : 'negative'">{{ counter }}</h2>    
    <div class="btn-group">
      <button @click="increment" class="btn btn-success">Aumentar</button> 
      <button @click="decrement" class="btn btn-danger">Disminuir</button> 
      <button @click="Reset" class="btn btn-secondary">Reset</button> 
      <button @click="add" :disabled="blockBtnAdd" class="btn btn-primary">Add</button> 

    </div>
    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="(num, index) in arrayFavoritos" :key="index">{{ num }}</li>
    </ul>
  </div>
</template>

<style>
  h1{ f
    color: red;
  }
  .positive{
    color: #0f0
  }
  .negative{
    color: #f00
  }
</style>