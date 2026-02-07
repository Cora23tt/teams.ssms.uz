<script setup>
import AppIcon from './AppIcon.vue';

const props = defineProps({
  items: { type: Array, required: true },
  modelValue: { type: String, required: true }
});

const emit = defineEmits(['update:modelValue']);

const setActive = (id) => {
  if (id !== props.modelValue) {
    emit('update:modelValue', id);
  }
};
</script>

<template>
  <nav class="bottom-nav" role="tablist" aria-label="Главное меню">
    <button
      v-for="item in items"
      :key="item.id"
      class="bottom-nav__item"
      :class="{ 'is-active': item.id === modelValue }"
      type="button"
      role="tab"
      :aria-selected="item.id === modelValue"
      :aria-current="item.id === modelValue ? 'page' : undefined"
      @click="setActive(item.id)"
    >
      <span class="bottom-nav__icon" aria-hidden="true">
        <AppIcon :name="item.icon" />
      </span>
      <span class="bottom-nav__label">{{ item.label }}</span>
    </button>
  </nav>
</template>
