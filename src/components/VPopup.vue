<template>
  <transition name="fade">
    <div class="popWrap">
      <div class="popWrapContent">
        <div class="popHeader">
          {{ 전달값 }}
          <button class="close" @click="closePopup"></button>
        </div>
        <div class="popContent">내용</div>
      </div>
    </div>
  </transition>
</template>

<script setup>
import { ref } from 'vue'

let popup = ref(false)

const closePopup = () => {
  popup.value = false
}
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
