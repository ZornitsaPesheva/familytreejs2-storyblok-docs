<script setup>
import { StoryblokRichText } from '@storyblok/vue';

defineProps({ blok: { type: Object, required: true } });
</script>

<template>
  <section v-editable="blok" class="code-example">
    <div v-if="blok.title || blok.description" class="code-example__intro">
      <h3 v-if="blok.title">{{ blok.title }}</h3>
      <div v-if="blok.description" class="code-example__description">
        <StoryblokRichText :doc="blok.description" />
      </div>
    </div>
    <div class="code-example__source">
      <div v-if="blok.language" class="code-example__language">{{ blok.language }}</div>
      <pre tabindex="0" :aria-label="blok.title || 'Code example'"><code :class="blok.language ? `language-${blok.language}` : undefined">{{ blok.code }}</code></pre>
    </div>
  </section>
</template>

<style scoped>
.code-example {
  box-sizing: border-box;
  width: 100%;
  max-width: 56rem;
  min-width: 0;
  margin: 2rem auto;
  border: 1px solid #cbd5e1;
  border-radius: 0.75rem;
  color: #1e293b;
  font-family: system-ui, sans-serif;
  line-height: 1.7;
}
.code-example__intro { padding: clamp(1rem, 4vw, 1.5rem); overflow-wrap: anywhere; }
h3 { margin: 0 0 0.75rem; font-size: 1.25rem; line-height: 1.35; }
.code-example__description :deep(> :first-child) { margin-top: 0; }
.code-example__description :deep(> :last-child) { margin-bottom: 0; }
.code-example__description :deep(a) { color: #1d4ed8; text-underline-offset: 0.2em; }
.code-example__description :deep(img) { max-width: 100%; height: auto; }
.code-example__description :deep(pre) { overflow-x: auto; }
.code-example__source { background: #0f172a; color: #e2e8f0; border-radius: 0 0 0.7rem 0.7rem; }
.code-example__source:first-child { border-radius: 0.7rem; }
.code-example__language { padding: 0.5rem 1rem; border-bottom: 1px solid #334155; font-size: 0.8rem; overflow-wrap: anywhere; }
pre { margin: 0; padding: clamp(1rem, 4vw, 1.5rem); overflow-x: auto; border-radius: inherit; }
pre:focus-visible { outline: 2px solid #60a5fa; outline-offset: -3px; }
.code-example {
  color: #f5f5f5;
}

.code-example h3 {
  color: #ffffff;
}

.code-example :deep(p),
.code-example :deep(li) {
  color: #f5f5f5;
}

.code-example pre {
  background: #111827;
  color: #f8fafc;
}

.code-example code {
  color: #f8fafc;
}code { font-family: ui-monospace, SFMono-Regular, Consolas, monospace; font-size: 0.875rem; line-height: 1.65; white-space: pre; tab-size: 2; }
.code-example {
  color: #f5f5f5;
}


</style>
