<template>
  <button class="btn" type="button">
    <slot />
  </button>
</template>

<script></script>

<style scoped>
.btn {
  padding: 4px 8px;
  border-radius: 8px;
  background-color: transparent;
  transition: background-color 250ms cubic-bezier(0.47, 0, 0.745, 0.715);
  cursor: pointer;
}
.btn:hover {
  background-color: aqua;
}
.btn:disabled {
  background-color: red;
}
</style>
