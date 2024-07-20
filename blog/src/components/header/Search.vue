<template>
  <div class="search">
    <img src="@/assets/search.svg" />
    <input
      placeholder="Search"
      :value="search"
      @input="
        if (searchModifiers?.trim) {
          $emit('update:search', $event.target.value.trim());
        } else {
          $emit('update:search', $event.target.value);
        }
      "
    />
  </div>
</template>

<script setup>
defineProps(["search", "searchModifiers"]);
defineEmits(["update:search"]);
</script>

<style scoped>
.search {
  background-color: #333;
  position: relative;
  margin-top: 10px;
  padding: 1px 3px;
}

.search img {
  position: absolute;
  height: 50%;
  top: 50%;
  transform: translate(7px, -50%);
}

input {
  border: 0;
  padding-left: 25px;
}
</style>
