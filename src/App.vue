<template>
  <TopNav :windowWidth="windowWidth" />
  <div class="main">
    <div class="cards-section">
      <h1 class="title">Photo Cards:</h1>
      <div :class="`grid-container`">
        <template v-for="i in 30">
          <ItemCard :img-url="images[Math.floor(Math.random() * 2)]" />
        </template>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';
import TopNav from './components/TopNav.vue';
import ItemCard from './components/ItemCard.vue';

const debounce = (func: Function, wait: number) => {
  let timeout: number;
  return (...args: any[]) => {
    clearTimeout(timeout);
    timeout = window.setTimeout(() => func(...args), wait);
  };
};

const images: string[] = [
  "https://imgur.com/unmma82.jpeg",
  "https://imgur.com/2MM9Jqo.png"
]

const windowWidth = ref<number>(window.innerWidth);

const handleResize = debounce(() => {
  windowWidth.value = window.innerWidth;
}, 100);

onMounted(() => {
  window.addEventListener('resize', handleResize)
  handleResize();
});

onUnmounted(() => {
  window.removeEventListener('resize', handleResize)
});
</script>