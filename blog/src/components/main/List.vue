<template>
  <ul class="list">
    <li
      v-for="post of filteredList"
      :key="post.id"
      @click="
        $emit('change-id', post.id);
        updateName('Post');
      "
    >
      <span>{{ post.title }}</span>
      <span class="category" v-bind:class="post.category.toLowerCase()">
        {{ post.category }}
      </span>
    </li>
  </ul>
</template>

<script setup>
import { getPageTable } from "vue-notion";
import { ref, computed, inject } from "vue";

const list = ref([]);

const { updateName } = inject("name");
const { category } = inject("category");

const props = defineProps(["keyword"]);
const filteredList = computed(() => {
  return list.value.filter((item) => {
    return (
      (item.category == category.value || category.value == "") &&
      item.title.includes(props.keyword)
    );
  });
  // return list.value.filter((item) => {
  //   return item.category == category.value || category.value == "";
  // });
  // return list.value.filter((item) => {
  //   return item.title.includes(keyword.value);
  // });
});

getPageTable("283692adcaff4a9ebc11cf34c38e38d7").then((value) => {
  list.value = value;
});
</script>

<style>
.list {
  list-style-type: none;
  padding: 0;
  border: 1px solid #ddd;
}

.list li {
  border-bottom: 1px solid #ddd;
  padding: 10px;
  display: flex;
}

.list li:hover {
  background-color: #eee;
  cursor: pointer;
}

.list .category {
  margin-left: auto;
  color: white;
  border-radius: 5px;
  padding: 2px 5px;
}

.list .category.html {
  background-color: coral;
}

.list .category.css {
  background-color: cornflowerblue;
}

.list .category.javascript {
  background-color: gold;
}
</style>
