<script setup>
import { StoryblokRichText } from '@storyblok/vue';

defineProps({ blok: { type: Object, required: true } });
</script>

<template>
  <section v-editable="blok" :id="blok.anchor || undefined" class="docs-section">
    <h2 v-if="blok.title">{{ blok.title }}</h2>
    <div v-if="blok.content" class="docs-section__content">
      <StoryblokRichText :doc="blok.content" />
    </div>
  </section>
</template>

<style scoped>
.docs-section {
  box-sizing: border-box;
  width: 100%;
  max-width: 56rem;
  min-width: 0;
  margin: 2rem auto;
  padding: clamp(1rem, 4vw, 2rem);
  color: #1e293b;
  font-family: system-ui, sans-serif;
  line-height: 1.75;
  overflow-wrap: anywhere;
  scroll-margin-top: 5rem;
  border-bottom: 1px solid #e2e8f0;
}
h2 {
  margin: 0 0 1rem;
  font-size: clamp(1.5rem, 4vw, 2rem);
  line-height: 1.25;
  letter-spacing: -0.025em;
}
.docs-section__content :deep(> :first-child) { margin-top: 0; }
.docs-section__content :deep(> :last-child) { margin-bottom: 0; }
.docs-section__content :deep(a) { color: #1d4ed8; text-underline-offset: 0.2em; }
.docs-section__content :deep(img) { max-width: 100%; height: auto; }
.docs-section__content :deep(pre) { overflow-x: auto; padding: 1rem; background: #f1f5f9; border-radius: 0.5rem; }
.docs-section__content :deep(code) { font-family: ui-monospace, monospace; font-size: 0.9em; }
.docs-section__content :deep(blockquote) { margin-inline: 0; padding-left: 1rem; border-left: 3px solid #cbd5e1; }

.docs-section {
  color: #f5f5f5;
}

.docs-section h2 {
  color: #ffffff;
}

.docs-section :deep(p),
.docs-section :deep(li) {
  color: #e5e7eb;
}

.docs-section :deep(a) {
  color: #a5b4fc;
}
</style>
