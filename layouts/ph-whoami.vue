<script setup lang="ts">
withDefaults(defineProps<{
  name?: string
  handle?: string
  photo?: string
  talk?: string
  track?: string
  when?: string
}>(), {
  name: 'Daniel Reis',
  handle: '@danielhe4rt',
  photo: 'https://github.com/danielhe4rt.png',
  talk: 'Laravel Modular na Prática: como organizar um monolito sem virar uma bomba',
  track: 'Arquitetura',
  when: 'Sexta · 16/10',
})
</script>

<template>
  <div class="ph-slide ph-slide--orange ph-whoami">
    <header class="ph-topbar ph-rise">
      <img class="ph-topbar__logo" src="/images/phpeste-logo-espresso.png" alt="PHPeste 2026">
      <span class="ph-topbar__fill" />
      <span class="ph-topbar__meta">
        <mdi-calendar-blank-outline aria-hidden="true" />{{ when }}
      </span>
    </header>

    <div class="ph-whoami__body">
      <!-- speaker card, same shape as the site's "Palestrantes" grid -->
      <figure class="ph-speaker ph-rise ph-rise--1">
        <div class="ph-speaker__frame">
          <svg class="ph-speaker__sun" viewBox="0 0 40 40" aria-hidden="true">
            <circle cx="20" cy="20" r="6" />
            <path d="M20 2v8M20 30v8M2 20h8M30 20h8M7 7l6 6M27 27l6 6M33 7l-6 6M13 27l-6 6" />
          </svg>
          <div class="ph-speaker__arch">
            <img :src="photo" :alt="`Foto de ${name}`">
          </div>
        </div>
        <figcaption class="ph-speaker__info">
          <span class="ph-speaker__name">{{ name }}</span>
          <span class="ph-speaker__handle">{{ handle }}</span>
          <span class="ph-speaker__talk">{{ talk }}</span>
          <span class="ph-speaker__track">
            <mdi-bank-outline aria-hidden="true" />{{ track }}
          </span>
        </figcaption>
      </figure>

      <div class="ph-whoami__content ph-rise ph-rise--2">
        <slot />
      </div>
    </div>

    <div class="ph-azulejo" aria-hidden="true" />
  </div>
</template>

<style src="../styles/phpeste.css"></style>

<style>
.ph-whoami__body {
  flex: 1;
  display: grid;
  grid-template-columns: 15.5rem 1fr;
  gap: 2.4rem;
  align-items: center;
  padding: 0.6rem 2.6rem 1.4rem;
  min-height: 0;
}

/* -------- speaker card -------- */
.ph-speaker {
  margin: 0;
  display: flex;
  flex-direction: column;
  border: 1.5px solid rgba(35, 18, 8, 0.35);
  border-radius: 4px;
  overflow: hidden;
  background: var(--ph-orange-lt);
  box-shadow: 0 10px 28px rgba(35, 18, 8, 0.25);
}
.ph-speaker__frame {
  position: relative;
  height: 13rem;
  background: var(--ph-espresso);
  display: flex;
  align-items: flex-end;
  justify-content: center;
}
.ph-speaker__sun {
  position: absolute;
  top: 0.8rem;
  left: 0.8rem;
  width: 2rem;
  fill: var(--ph-orange);
  stroke: var(--ph-orange);
  stroke-width: 2.5;
  stroke-linecap: round;
}
.ph-speaker__arch {
  width: 78%;
  height: 88%;
  border-radius: 999px 999px 0 0;
  overflow: hidden;
  background: var(--ph-sand);
}
.ph-speaker__arch img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}
.ph-speaker__info {
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
  padding: 0.9rem 1rem 1rem;
  color: var(--ph-espresso);
}
.ph-speaker__name { font-size: 1.2rem; font-weight: 600; line-height: 1.2; }
.ph-speaker__handle { font-family: var(--ph-font-mono); font-size: 0.8rem; margin-top: -0.2rem; }
.ph-speaker__talk { font-size: 0.85rem; font-style: italic; line-height: 1.4; }
.ph-speaker__track {
  display: inline-flex;
  align-items: center;
  gap: 0.35rem;
  margin-top: 0.2rem;
  font-size: 0.8rem;
}

/* -------- right column (default slot) -------- */
.ph-whoami__content { display: flex; flex-direction: column; gap: 0.9rem; min-width: 0; }
.ph-whoami__content h1 {
  margin: 0;
  font-family: var(--ph-font-display);
  font-weight: 400;
  font-size: 3.4rem;
  line-height: 1;
  color: var(--ph-espresso);
}
.ph-whoami__content p {
  margin: 0;
  font-size: 1.1rem;
  line-height: 1.5;
}
.ph-whoami__content p strong { font-weight: 600; }

.ph-whoami__content li strong { font-weight: 600; }

.ph-whoami__socials {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 0.5rem 1.1rem;
  font-family: var(--ph-font-ui);
  font-size: 0.85rem;
  font-weight: 600;
}
.ph-whoami__socials span { display: inline-flex; align-items: center; gap: 0.35rem; }
.ph-whoami__socials .ph-mono { font-weight: 600; }
</style>
