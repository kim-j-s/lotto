<template>
  <div class="rstBox">
    <template v-for="(box, index) in 전달값" :key="index">
      <label class="rstBoxLabel">
        <input type="radio" name="rstGroup" :value="index" :checked="index === radioCheck" />
        <div class="doms">
          <slot v-if="numView">
            <span class="listNum"> {{ index + 1 }}. </span>
          </slot>
          <div class="domsRst">
            <span
              v-for="(item, idx) in box"
              :key="idx"
              class="round"
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
      </label>
    </template>
  </div>
</template>

<script setup>
import { ref, onUpdated } from 'vue'

// props로 받은 sendValue
const props = defineProps({
  전달값: {
    type: Array
  },
  numView: {
    type: Boolean
  }
})

// radio Checkbox 초기화 선언
const radioCheck = ref(0)
const 선택으로변경 = (index) => {}

// const rstBoxes = ref([])

onUpdated(() => {
  console.log('값이 바뀜 onUpdated', props.전달값)
})
</script>

<style lang="scss" scoped></style>
