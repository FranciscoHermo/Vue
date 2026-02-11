<script setup>
import { useFavoritosStore } from "@/store/favoritos";
import { storeToRefs } from "pinia";

const useFavoritos = useFavoritosStore();

const { favoritos } = storeToRefs(useFavoritos);
</script>

<template>
  <h1>Favoritos</h1>
  <ul class="list-group">
    <li class="list-group-item" v-for="poke in favoritos" :key="poke.id"> {{ poke.name }}</li>
  </ul>
</template>
