<template>
  <button
    type="button"
    role="checkbox"
    :aria-checked="checked"
    :data-state="checked ? 'checked' : 'unchecked'"
    :class="[
      'peer h-4 w-4 shrink-0 rounded-sm border border-primary ring-offset-background focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50 data-[state=checked]:bg-primary data-[state=checked]:text-primary-foreground',
      className
    ]"
    @click="toggle"
  >
    <span
      v-if="checked"
      class="flex h-full w-full items-center justify-center text-current"
    >
      <svg
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
        class="h-4 w-4"
      >
        <polyline points="20 6 9 17 4 12" />
      </svg>
    </span>
  </button>
</template>

<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps<{
  modelValue?: boolean
  className?: string
}>()

const emit = defineEmits<{
  (e: 'update:modelValue', value: boolean): void
}>()

const checked = computed({
  get: () => props.modelValue ?? false,
  set: (value) => emit('update:modelValue', value)
})

const toggle = () => {
  checked.value = !checked.value
}
</script> 