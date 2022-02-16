<script>
export default {};
</script>

<template>
  <ul class="list">
    <slot />
  </ul>
</template>

<style scoped>
.list {
  list-style: none;

  display: grid;
  max-width: calc(100vw - 48px);
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  grid-gap: 16px;
  padding: 0;
  margin: 0 auto;
}
</style>
