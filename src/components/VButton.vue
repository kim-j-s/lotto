<template>
  <button class="btn">
    <span class="text">{{ text }}</span>
  </button>
</template>

<script setup>
defineProps({
  text: {
    type: String
  }
})
</script>

<style lang="scss" scoped></style>
