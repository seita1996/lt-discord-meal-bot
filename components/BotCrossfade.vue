<script setup lang="ts">
import { computed } from 'vue'
import { useSlideContext } from '@slidev/client'

import botFirst from '../assets/bot-first.png'
import botPlan from '../assets/bot-plan.png'
import botThinking from '../assets/bot-thinking.png'
import botDone from '../assets/bot-done.png'
import botShoplist from '../assets/bot-shoplist.png'

const images = [botFirst, botPlan, botThinking, botDone, botShoplist]
const { $clicks } = useSlideContext()
const activeIndex = computed(() => Math.min($clicks.value, images.length - 1))
</script>

<template>
  <div class="bot-crossfade">
    <div class="bot-click-steps" aria-hidden="true">
      <span v-for="idx in images.length - 1" :key="`step-${idx}`" v-click />
    </div>
    <img
      v-for="(src, idx) in images"
      :key="src"
      :src="src"
      :class="['bot-crossfade-image', { active: idx === activeIndex }]"
      alt="Bot flow image"
    />
  </div>
</template>

<style scoped>
.bot-crossfade {
  width: min(640px, 92vw);
  margin-inline: auto;
  display: grid;
}

.bot-click-steps {
  position: absolute;
  width: 0;
  height: 0;
  overflow: hidden;
  opacity: 0;
  pointer-events: none;
}

.bot-crossfade-image {
  grid-area: 1 / 1;
  width: 100%;
  height: auto;
  border-radius: 14px;
  opacity: 0;
  transform: scale(0.985);
  transition:
    opacity 480ms ease,
    transform 480ms ease;
  box-shadow: 0 14px 36px rgb(2 6 23 / 32%);
}

.bot-crossfade-image.active {
  opacity: 1;
  transform: scale(1);
}
</style>
