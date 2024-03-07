<template>
  <div class="rstBox">
    <div class="doms" v-for="(box, index) in 전달값" :key="index">
      <span
        v-for="(item, idx) in box"
        :key="idx"
        :class="{
          color1: item < 11,
          color2: item >= 11 && item < 21,
          color3: item >= 21 && item < 31,
          color4: item >= 31 && item < 41,
          color5: item >= 41 && item < 46
        }"
        >{{ item }}</span
      >
    </div>
  </div>
</template>

<script setup>
import { ref, onUpdated } from 'vue'

// props로 받은 sendValue
const props = defineProps({
  전달값: {
    type: Array
  }
})

// const rstBoxes = ref([])

onUpdated(() => {
  console.log('값이 바뀜 onUpdated', props.전달값)
})
</script>

<style lang="scss" scoped></style>
