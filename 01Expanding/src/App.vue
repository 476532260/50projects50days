<template>
  <div class="container">
    <div class="panel"
     v-for="(item, index) in images"
     :key="index"
     :class="index === currentIndex ? 'active' : ''" 
     :style="{backgroundImage: `url(${item})`}" 
     @click="currentIndex = index">
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const images = [
  'https://images.unsplash.com/photo-1558979158-65a1eaa08691?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80',
  'https://images.unsplash.com/photo-1572276596237-5db2c3e16c5d?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80',
  'https://images.unsplash.com/photo-1507525428034-b723cf961d3e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1353&q=80',
  'https://images.unsplash.com/photo-1551009175-8a68da93d5f9?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1351&q=80',
  'https://images.unsplash.com/photo-1549880338-65ddcdfd017b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80'
]
const currentIndex = ref(0)
</script>

<style lang="scss">
body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  overflow: hidden;
  margin: 0;
  padding: 0;
}
.container {
  display: flex;
  width: 90vw;
  .panel {
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    height: 80vh;
    border-radius: 50px;
    color: #fff;
    cursor: pointer;
    flex: 0.5;
    margin: 10px;
    position: relative;
    transition: all 0.7s ease-in;
    -webkit-transform: all 0.7s ease-in;
    &.active {
      flex: 5;
    }
  }
}
</style>

