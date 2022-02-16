<script setup>
import { inject } from "vue";

const contacts = inject("contacts");
const visibleContacts = inject("visibleContacts");

const changeFilter = (e) => {
  const filter = e.target.value;
  console.log(filter);

  visibleContacts.value = [...visibleContacts.value].filter((el) =>
    el.name.includes(filter)
  );

  console.log(contacts.value);
  console.log(visibleContacts.value);
};
</script>

<template>
  <div class="wrapper">
    <h3 class="title">Filter</h3>
    <input type="text" @input="changeFilter" />
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
