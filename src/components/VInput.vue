<template>
  <div class="input">
    <!-- 부모에서 자식으로 보내는 value는 modelValue로 받아야 한다. -->
    <input
      :class="inpClass"
      :type="types"
      :value="modelValue"
      :maxlength="maxlengths"
      :placeholder="placeholder"
      @input="updateInputValue"
      @focus="iptFoucs"
    />
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
  placeholder: {
    type: String,
    default: '입력'
  }
})

// 값 전달
const emit = defineEmits(['update:modelValue'])
const updateInputValue = (event) => {
  emit('update:modelValue', event.target.value)
}

// input 초기화
const iptFoucs = (event) => {
  event.target.value = ''
  console.log('focus', event.target.value)
}
</script>

<style lang="scss" scoped></style>
