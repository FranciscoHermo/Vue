<script setup>
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "./components/HelloWorld.vue";
</script>

<template>
  <nav class="navbar bg-light">
    <div class="container">
      <RouterLink class="navbar-brand" to="/">
        <img
          src="@/assets/logo.svg"
          alt=""
          width="30"
          height="24"
          class="d-inline-block align-text-top"
        />
        Bootstrap
      </RouterLink>
      <div>
        <RouterLink class="btn btn-outline-primary" to="/">Home</RouterLink>
        <RouterLink class="btn btn-outline-primary" to="/pokemons"
          >Pokemons</RouterLink
        >
      </div>
    </div>
  </nav>
  <div class="container">
    <RouterView />
  </div>
</template>
