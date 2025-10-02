<script setup lang="ts">
import { ref, computed } from 'vue'

const currentIndex = ref(0)
const totalImages = 44

const currentImage = computed(() => {
  const num = (currentIndex.value + 1).toString().padStart(3, '0')
  return `/images/${num}.jpg`
})

const prev = () => {
  if (currentIndex.value > 0) {
    currentIndex.value--
  }
}

const next = () => {
  if (currentIndex.value < totalImages - 1) {
    currentIndex.value++
  }
}
</script>

<template>
  <div class="carousel">
    <img :src="currentImage" :alt="`Image ${currentIndex + 1}`" />
    <div class="click-area left" @click="prev"></div>
    <div class="click-area right" @click="next"></div>
  </div>
</template>

<style scoped>
.carousel {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: #000;
  overflow: hidden;
}

img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  user-select: none;
  -webkit-user-drag: none;
}

.click-area {
  position: absolute;
  top: 0;
  height: 100%;
  width: 50%;
  cursor: pointer;
}

.click-area.left {
  left: 0;
}

.click-area.right {
  right: 0;
}
</style>
