<template>
  <main>
    <!--component :is="comp[name]" /-->
    <List
      v-if="name == 'List'"
      @change-id="
        (newId) => {
          id = newId;
        }
      "
      :keyword="keyword"
    />
    <Post v-if="name == 'Post'" :id="id" />
  </main>
</template>

<script setup>
import { ref, defineAsyncComponent, inject } from "vue";

defineProps(["keyword"]);

const { name } = inject("name");

const id = ref("91caab9a9bc945309802175ab9f7d32d");

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
