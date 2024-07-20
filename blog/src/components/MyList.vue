<template>
  <ul>
    <li v-for="item of list" :key="item">
      <slot v-bind="item"></slot>
    </li>
  </ul>
</template>

<script setup>
defineProps(["list"]);
</script>

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
  display: flex;
}
li {
  margin-left: 10px;
}
</style>
