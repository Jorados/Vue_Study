<template>
  <input ref="search" />
</template>

<script setup>
import { ref, onMounted } from "vue";

const search = ref(null);

onMounted(() => {
  search.value.focus();
});
</script>

<style scoped>
input {
  margin-top: 10px;
}
</style>
