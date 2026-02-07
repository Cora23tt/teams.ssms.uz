<script setup>
defineProps({
  title: { type: String, required: true },
  subtitle: { type: String, default: '' },
  meta: { type: String, default: '' }
});
</script>

<template>
  <article class="app-card">
    <header class="app-card__header">
      <div>
        <p class="app-card__eyebrow" v-if="meta">{{ meta }}</p>
        <h3 class="app-card__title">{{ title }}</h3>
        <p class="app-card__subtitle" v-if="subtitle">{{ subtitle }}</p>
      </div>
    </header>
    <div class="app-card__body">
      <slot />
    </div>
    <footer class="app-card__actions" v-if="$slots.actions">
      <slot name="actions" />
    </footer>
  </article>
</template>
