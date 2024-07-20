<template>
  <header>
    <img src="@/assets/logo.jpg" ref="logo" />

    <Search />

    <nav>
      <a v-for="item of menu" :key="item">
        {{ item }}
      </a>
    </nav>
  </header>
</template>

<script setup>
import Search from "@/components/header/Search.vue";
import { ref, onMounted } from "vue";

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
