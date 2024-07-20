<template>
  <footer>
    <span>Made by <strong>Blog Creator</strong></span>
    <MyList :list="list" class="sns-link">
      <template #default="item">
        <a :href="item.href">
          <img :src="item.src" />
        </a>
      </template>
    </MyList>
  </footer>
</template>

<script setup>
import MyList from "@/components/MyList.vue";

const list = [
  {
    src: new URL("@/assets/sns_github.png", import.meta.url).href,
    href: "",
  },
  {
    src: new URL("@/assets/sns_instagram.png", import.meta.url).href,
    href: "",
  },
  {
    src: new URL("@/assets/sns_youtube.png", import.meta.url).href,
    href: "",
  },
];
</script>

<style scoped>
footer {
  width: 80%;
  margin: 10px auto;

  display: flex;
}
footer img {
  height: 25px;
}

.sns-link {
  margin-left: auto;
}
</style>
