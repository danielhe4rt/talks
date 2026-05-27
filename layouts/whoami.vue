<!--
  Who Am I layout — profile card with avatar and bio.

  Usage:
  ```md
  ---
  layout: whoami
  image: https://github.com/user.png
  handle: username
  ---

  # Name

  Bio text and bullet points here
  ```
-->

<script setup lang="ts">
defineProps({
  image: { type: String, default: '' },
  handle: { type: String, default: '' },
  full_name: { type: String, default: '' },
  has_socials: { type: Boolean, default: false },
  class: { type: String },
})
</script>

<template>
  <div class="slidev-layout whoami">
    <div class="whoami__avatar-col">
      <div class="whoami__avatar-ring">
        <img
          v-if="image"
          :src="image"
          :alt="handle || 'avatar'"
          class="whoami__avatar-img"
        />
      </div>

      <div v-if="handle" class="whoami__handle">
        @{{ handle }}
      </div>
    </div>

    <div class="whoami__bio" :class="$props.class">
      <slot />
    </div>
  </div>
</template>

<style scoped>
.whoami {
  display: grid;
  grid-template-columns: 220px 1fr;
  gap: 2.5rem;
  height: 100%;
  width: 100%;
  padding: 2.5rem 3rem;
  align-items: center;
}

.whoami__avatar-col {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}

.whoami__avatar-ring {
  width: 180px;
  height: 180px;
  border-radius: 50%;
  padding: 4px;
  background: linear-gradient(
    135deg,
    var(--slidev-theme-primary) 0%,
    #4EC5D4 50%,
    #146b8c 100%
  );
  flex-shrink: 0;
}

.whoami__avatar-img {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  object-fit: cover;
  display: block;
}

.whoami__handle {
  font-family: var(--slidev-code-font-family, 'Fira Code', monospace);
  font-size: 0.9rem;
  opacity: 0.5;
  letter-spacing: 0.02em;
}

.whoami__bio {
  overflow-y: auto;
  max-height: 100%;
}

.whoami__bio :deep(h1) {
  font-size: 1.75rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  background: linear-gradient(135deg, #4EC5D4 10%, #146b8c 60%);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.whoami__bio :deep(ul) {
  list-style: none;
  padding: 0;
  margin: 0;
}

.whoami__bio :deep(li) {
  font-size: 0.85rem;
  line-height: 1.7;
  padding: 0.1rem 0;
}

.whoami__bio :deep(blockquote) {
  margin-top: 1rem;
  padding: 0.5rem 1rem;
  border-left: 3px solid var(--slidev-theme-primary);
  opacity: 0.7;
  font-size: 0.8rem;
}
</style>
