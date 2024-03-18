<template>
  <div class="input">
    <!-- 부모에서 자식으로 보내는 value는 modelValue로 받아야 한다. -->
    <input
      :class="inpClass"
      :type="types"
      :maxlength="maxlengths"
      :max="max"
      :placeholder="placeholder"
      @focus="iptFoucs"
      v-model="childValue"
    />
    <!-- :value="modelValue" -->
    <!-- @input="updateInputValue" -->
  </div>
</template>

<script setup>
defineProps({
  inpClass: {
    type: String
  },
  types: {
    type: String,
    default: 'text'
  },
  modelValue: {
    type: String
  },
  maxlengths: {
    type: String,
    default: 50
  },
  max: {
    type: String
  },
  placeholder: {
    type: String,
    default: '입력'
  }
})

// 값 전달
// const emit = defineEmits(['update:modelValue'])
// const updateInputValue = (event) => {
//   emit('update:modelValue', event.target.value)
// }

const childValue = defineModel()

// input 초기화
const iptFoucs = (event) => {
  event.target.value = ''
}
</script>

<style lang="scss" scoped></style>
