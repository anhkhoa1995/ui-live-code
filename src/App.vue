<template>
  <div class="header">
    <TopNav />
  </div>
  <div class="main">
    <div class="container">
      <h1 class="title">Photo Cards:</h1>
      <div :class="`grid-container cols-${columns}`">
        <template v-for="i in 30">
          <ItemCard :img-url="images[Math.floor(Math.random() * 2)]"
            :width-content="(windowWidth - ((columns + 1) * 15)) / columns" />
        </template>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';
import TopNav from './components/TopNav.vue';
import ItemCard from './components/ItemCard.vue';

const images: string[] = [
  "https://imgur.com/unmma82.jpeg",
  "https://imgur.com/2MM9Jqo.png"
]

const getNumberOfColumns = (): number => {
  const width = window.innerWidth;
  if (width <= 480) {
    return 1;
  } else if (width <= 768) {
    return 2;
  } else if (width <= 1024) {
    return 4;
  } else {
    return 6;
  }
};

const columns = ref<number>(getNumberOfColumns());
const windowWidth = ref<number>(window.innerWidth);

const updateColumns = (): void => {
  columns.value = getNumberOfColumns();
};
const updateWindowWidth = (): void => {
  windowWidth.value = window.innerWidth > 1399 ? 1320 : window.innerWidth;
};
const handleResize = (): void => {
  updateWindowWidth();
  updateColumns();
};

onMounted(() => {
  window.addEventListener('resize', handleResize);
  handleResize();
});

onUnmounted(() => {
  window.removeEventListener('resize', handleResize);
});
</script>