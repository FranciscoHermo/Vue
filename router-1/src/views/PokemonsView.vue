<script setup>
import axios from 'axios';
import { ref } from 'vue';
import {RouterLink} from 'vue-router'

const pokemos = ref([])

const getData = async() => {
    try{
        const {data} = await axios.get('https://pokeapi.co/api/v2/pokemon')
        console.log(data.results)
        pokemos.value = data.results
    } catch(error){
        console.log(error)
    }
}

getData()

</script>

<template>
    <h1>Pokemos</h1>
    <ul>
        <li v-for="poke in pokemos" >
            <RouterLink :to="`/pokemons/${poke.name}`">{{ poke.name }}</RouterLink>
        </li>
    </ul>
</template>