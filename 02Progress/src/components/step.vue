<template>
  <div class="step-container">
    <div class="step-progress"></div>
    <slot></slot>
  </div>
</template>

<script lang="ts" setup>
import { computed } from 'vue'
const props = defineProps({
  width: {
    type: Number,
    default: 350
  },
  progressWidth: {
    type: Number,
    default: 0
  }
})
const styleWidth = computed(() => props.width + 'px')
const styleProgressWidth = computed(() => props.progressWidth + '%')
</script>

<style lang="scss" scoped>
.step-container {
  display: flex;
  justify-content: space-between;
  box-sizing: border-box;
  width: v-bind('styleWidth');
  margin-bottom: 30px;
  position: relative;
  &::before, .step-progress {
    height: 5px;
    left: 0;
    z-index: -1;
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
  }
  &:before {
    content: '';
    width: 100%;
    background: #383838;
  }
  .step-progress {
    background: #3498db;
    transition: 0.4s ease;
    width: v-bind(styleProgressWidth);
  }
}
</style>