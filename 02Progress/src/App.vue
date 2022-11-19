<template>
  <div class="container">
    <div class="container-top">
      <step :progressWidth="pWidth">
        <step-item
          v-for="(item, index) in state.stepList"
          :key="index"
          :class="{ active: state.current >= index }"
        >{{item.value}}</step-item>
      </step>
    </div>
    <div class="container-bottom">
      <button class="btn" :disabled="state.current === 0" @click="handlePrev">上一步</button>
      <button class="btn" :disabled="state.current === state.stepList.length - 1" @click="handleNext">下一步</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive, computed } from 'vue'
import step from './components/step.vue'
import stepItem from './components/step-item.vue'
const state = reactive({
  stepList: [
    { value: 1 },
    { value: 2 },
    { value: 3 },
    { value: 4 }
  ],
  current: 0
})
const pWidth = computed(() => Math.floor(100 / 3) * state.current)
const handlePrev = () => {
  if (state.current <= 0) {
    return
  }
  state.current--
}
const handleNext = () => {
  if (state.current > state.stepList.length - 1) {
    return
  }
  state.current++
}
</script>

<style lang="scss">
body {
  margin: 0;
  padding: 0;
}

.container {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.btn {
  background: #3498db;
  color: #fff;
  border: 0;
  border-radius: 6px;
  cursor: pointer;
  padding: 8px 30px;
  margin: 5px;
  font-size: 14px;
  &:active {
    transform: scale(0.98);
  }
  &:focus {
    outline: 0;
  }
  &:disabled {
    background: #383838;
    cursor: not-allowed;
  }
}
</style>
