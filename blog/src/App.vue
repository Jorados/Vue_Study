<template>
  <SiteHeader v-model="keyword" />
  <SiteMain :keyword="keyword" />
  <SiteFooter />
  <div class="my-loader" v-show="loading">
    <Loading />
  </div>
</template>

<script setup>
import SiteHeader from "./components/SiteHeader.vue";
import Loading from "@/components/Loading.vue";
import SiteFooter from "./components/SiteFooter.vue";
import SiteMain from "@/components/SiteMain.vue";

import { ref, onMounted, provide } from "vue";

const keyword = ref("");
const loading = ref(true);
const name = ref("List");
const category = ref("");

provide("name", {
  name,
  updateName(newName) {
    name.value = newName;
  },
});

provide("category", {
  category,
  updateCategory(newCategory) {
    category.value = newCategory;
  },
});

onMounted(() => {
  setTimeout(() => {
    loading.value = false;
  }, 500);
});
</script>

<style>
.my-loader {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.3);

  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
