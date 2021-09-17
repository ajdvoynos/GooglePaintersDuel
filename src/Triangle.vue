<script setup>
  import { defineProps } from "vue";

  const props = defineProps({
    rotate: Boolean,
    x: Number,
    y: Number
  });

</script>
<template>
  <svg height="100" width="100">
    <path :class="{'rotate': props.rotate}" fill="none" stroke="#ff0000" d="m0,100l50,-100l50,100l-100,0z" stroke-width="1"/>
    <text fill="#000000" stroke="#ff0000" stroke-width="0" x="25" :y="props.rotate ? 40 : 80" font-size="24" text-anchor="start" xml:space="preserve">({{x}},{{y}})</text>
  </svg>
</template>
<style>
  .rotate{
    transform: rotate(
180deg);
  }
</style>