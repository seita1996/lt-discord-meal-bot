<script setup lang="ts">
defineProps({
  class: {
    type: String,
    default: '',
  },
  layoutClass: {
    type: String,
    default: '',
  },
})
</script>

<template>
  <div class="slidev-layout two-cols w-full h-full grid grid-cols-2 gap-10" :class="layoutClass">
    <div class="col-left min-w-0" :class="$props.class">
      <slot />
      <slot name="left" />
    </div>
    <div class="col-right min-w-0" :class="$props.class">
      <slot name="right" />
    </div>
  </div>
</template>
