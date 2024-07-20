<template>
  <NotionRenderer :blockMap="blockMap" fullPage />
</template>

<script setup>
import { getPageBlocks, NotionRenderer } from "vue-notion";
import { ref } from "vue";

const blockMap = ref(null);

getPageBlocks("91caab9a9bc945309802175ab9f7d32d").then(
  (value) => (blockMap.value = value)
);
</script>

<style>
/* optional Notion-like styles */
@import "vue-notion/src/styles.css";

.notion-title {
  border-bottom: 1px solid #ddd;
}
</style>
