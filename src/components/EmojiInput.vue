<script setup lang="ts">
import { useVModel } from '@vueuse/core'
import { EmojiButton } from '@joeattardi/emoji-button'
import { onMounted, ref } from 'vue'
interface Props {
  modelValue: string | {}
  options: {}
}
const props = withDefaults(defineProps<Props>(), {
  modelValue: '',
  options: {},
})
const emit = defineEmits(['update:modelValue'])
const emojiModel = useVModel(props, 'modelValue', emit)
onMounted(() => {
  const picker = new EmojiButton(props.options)
  const btn = document.getElementById('btn') as HTMLButtonElement
  picker.on('emoji', (emoji) => {
    emojiModel.value = emoji
  })
  btn.addEventListener('click', () => {
    picker.togglePicker()
  })
})
</script>
<template>
  <div class="input-group">
    <input
      type="text"
      class="form-control"
      readonly
      :value="emojiModel.emoji"
    />
    <button class="btn btn-outline-secondary" type="button" id="btn">
      {{ modelValue ? modelValue.emoji : 'Select' }}
    </button>
  </div>
</template>
