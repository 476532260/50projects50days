<template>
  <div class="step-circle">
    <slot></slot>
  </div>
</template>

<script lang="ts" setup>

</script>

<style lang="scss" scoped>
.step-circle {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 3px solid #383838;
  background: #fff;
  transition: 0.4s ease;
  &.active {
    border-color: #3498db;
    color: #3498db;
  }
}
</style>