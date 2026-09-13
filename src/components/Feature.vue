<script setup>
defineProps({
  blok: Object
});
</script>

<template>
  <a
    v-if="blok.link?.url"
    v-editable="blok"
    :href="blok.link.url"
    class="feature"
  >
    {{ blok.name }}
  </a>

  <div
    v-else
    v-editable="blok"
    class="feature"
  >
    {{ blok.name }}
  </div>
</template>

<style scoped>
.feature {
  display: block;
  color: #111827;
  text-decoration: none;
  cursor: pointer;
}
</style>