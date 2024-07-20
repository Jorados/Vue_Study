<template>
  <header>
    <img src="@/assets/logo.jpg" ref="logo" />

    <Search
      :search="modelValue"
      :searchModifiers="{ trim: true }"
      @update:search="(newVal) => $emit('update:modelValue', newVal)"
    />

    <nav>
      <a
        v-for="item of menu"
        :key="item"
        @click="
          updateName('List');
          updateCategory(item);
        "
      >
        {{ item }}
      </a>
    </nav>
  </header>
</template>

<script setup>
import Search from "@/components/header/Search.vue";
import { ref, onMounted, inject } from "vue";

defineProps(["modelValue"]);
defineEmits(["update:modelValue"]);

const { updateName } = inject("name");
const { updateCategory } = inject("category");

const logo = ref(null);
onMounted(() => {
  logo.value.onmouseover = function () {
    logo.value.classList.add("hover");
  };
  logo.value.onmouseout = function () {
    logo.value.classList.remove("hover");
  };
});

const menu = ["HTML", "CSS", "Javascript"];
</script>

<style scoped>
header {
  display: flex;
  flex-direction: column;
  align-items: center;
}

img {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  transition: transform 0.7s;
}

.hover {
  transform: scale(1.2);
}

nav {
  margin-top: 20px;
  background-color: #333;
  color: white;
  width: 80%;
  padding: 5px 10px;
  border-radius: 5px;
}

a {
  margin-right: 10px;
  font-weight: bold;
  cursor: pointer;
}
</style>
