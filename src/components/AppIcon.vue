<script setup>
const props = defineProps({
  name: {type: String, required: true},
  fill: {type: Number, default: 0},
  weight: {type: Number, default: 500},
  grade: {type: Number, default: 0},
  opsz: {type: Number, default: 24},
  size: {type: Number, default: 22},
  color: {type: String, default: 'default'}
});

const styleVars = {
  '--icon-fill': props.fill,
  '--icon-wght': props.weight,
  '--icon-grad': props.grade,
  '--icon-opsz': props.opsz,
  '--icon-size': `${props.size}px`
};
</script>

<template>
  <span class="app-icon material-symbols-rounded" :class="`app-icon--${color}`" aria-hidden="true" :style="styleVars">
    {{ name }}
  </span>
</template>
