<script setup>
import { ref, computed, onMounted } from "vue";


import BlogPost from "./components/BlogPost.vue";
import PaginatePost from "./components/PaginatePost.vue";
import LoaddinSpinner from "./components/loaddinSpinner.vue";

const posts = ref([]);

const postXpage = 10;
const inicio = ref(0);
const fin = ref(postXpage);
const loadding = ref(true);

const favorito = ref("");

const cambiarFavorito = (title) => {
  favorito.value = title;
};

const next = () => {
  inicio.value += postXpage;
  fin.value += postXpage;
}

const prev = () => {
  inicio.value -= postXpage;
  fin.value -= postXpage;

}

// onMounted(async() => {
//   // loadding.value = true;
//   try{
//     const res = await fetch("https://jsonplaceholder.typicode.com/posts")
//     posts.value = await res.json()
//   } catch (error){
//     console.log(error)
//   } finally{
//     setTimeout(() => {
//     loadding.value=false;
//     }, 2000);
//   }
// });

fetch("https://jsonplaceholder.typicode.com/posts")
  .then(res => res.json())
  .then(data => {
    posts.value=data;
  })
  .catch((e) => console.lod(e))
  .finally(() => {
    setTimeout(() => {
      loadding.value= false
    }, 2000);
  })


const maxLength = computed (() => {posts.value.length})

</script>

<template>
  <LoaddinSpinner v-if="loadding"/>
  <div class="container">
    <h1>APP</h1>
    <h2>Mis Post Favorito : {{ favorito }}</h2>

    <PaginatePost @next="next" @prev="prev" :inicio="inicio" :fin="fin" class="mb-2" :maxLength="maxLength"/>
    <BlogPost
      v-for="post in posts.slice(inicio, fin)"
      :key="post.id"
      :title="post.title"
      :id="post.id"
      :body="post.body"
      :cambiarFavorito="cambiarFavorito"
      class="mb-2"
    />
  </div>
</template>
