<template>
  <transition-group name="expand">
    <slot />
  </transition-group>
</template>

<script setup></script>

<style>
.expand-enter-active,
.expand-leave-active {
  transition: all 500ms ease-in-out;
  overflow: hidden;
  max-height: 1000px;
}

.expand-enter-from,
.expand-leave-to {
  opacity: 0;
  max-height: 0px;
}
</style>
