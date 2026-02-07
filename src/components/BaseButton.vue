<script setup>
import {computed} from 'vue';

const props = defineProps({
  variant: {type: String, default: 'filled'}, // filled | tonal | outline | text
  size: {type: String, default: 'md'}, // sm | md | lg
  block: {type: Boolean, default: false},
  disabled: {type: Boolean, default: false}
});

const classes = computed(() => [
  'base-button',
  `base-button--${props.variant}`,
  `base-button--${props.size}`,
  props.block && 'base-button--block'
]);
</script>

<template>
  <button class="base-button__root" :class="classes" :disabled="disabled">
    <span class="base-button__label">
      <slot/>
    </span>
  </button>
</template>

<style scoped>
</style>