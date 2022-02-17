<script setup>
import { inject } from "vue";

let filter = inject("filter");

const changeFilterValue = (e) => {
  filter.value = e.target.value;
};
</script>

<template>
  <div class="wrapper">
    <h3 class="title">Filter</h3>
    <input type="text" @input="changeFilterValue" />
  </div>
</template>

<style scoped>
.wrapper {
  margin-bottom: 12px;
}
.title {
  font-weight: 500;
  margin-bottom: 8px;
}
input {
  padding: 4px 8px;
  border-radius: 8px;
}
</style>
