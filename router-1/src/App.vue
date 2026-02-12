<script setup>
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "./components/HelloWorld.vue";
</script>

<template>
  <nav class="navbar bg-dark navbar-dark">
    <div class="container">
      <RouterLink class="navbar-brand" to="/">
        <img
          src="@/assets/logo.svg"
          alt=""
          width="30"
          height="24"
          class="d-inline-block align-text-top"
        />
        PokeAPI
      </RouterLink>
      <div>
        <RouterLink class="btn btn-outline-primary me-2" to="/">Home</RouterLink>
        <RouterLink class="btn btn-outline-primary me-2" to="/pokemons">Pokemons</RouterLink>
        <RouterLink class="btn btn-outline-primary me-2" to="/favoritos">Favoritos</RouterLink>
      </div>
    </div>
  </nav>
  <div class="container text-center">
    <RouterView />
  </div>
</template>
