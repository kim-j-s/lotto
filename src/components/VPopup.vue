<template>
  <div class="popWrap">
    <div class="popWrapContent">
      <div class="popHeader">
        결과
        <button class="close" @click="closePopup"></button>
      </div>
      <div class="popContent">
        <slot name="popContent"></slot>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import VRst from './VRst.vue'

// set
// 결과 값 전달
let sendValue = ref([])

defineProps({
  전달값: {
    type: Array
  }
})

const emits = defineEmits(['자식에서값올리는함수'])
const closePopup = () => {
  const popClose = false
  emits('자식에서값올리는함수', popClose)
  // 이케 올려도 됨
  // emits('자식에서값올리는함수', false)
}

// 닫기
// const closePopup = () => {
//   popup.value = false
// }
</script>

<style lang="scss" scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
