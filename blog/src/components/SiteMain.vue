<template>
  <main>
    <component :is="comp[name]" />
    <button @click="name = 'List'">List</button>
    <button @click="name = 'Post'">Post</button>
  </main>
</template>

<script setup>
import { ref, defineAsyncComponent } from "vue";

const name = ref("");

const List = defineAsyncComponent(() => import("@/components/main/List.vue"));
const Post = defineAsyncComponent(() => import("@/components/main/Post.vue"));

const comp = { List, Post };
</script>

<style scoped>
main {
  width: 80%;
  margin: 10px auto;
}
</style>
