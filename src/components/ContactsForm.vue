<script setup>
import { inject } from "vue";
import SubmitBtn from "./UI/SubmitBtn.vue";

const PLACEHOLDER = {
  NAME: "Contact name",
  PHONE: "Contact number",
};

const addContact = inject("addContact");
</script>

<template>
  <form @submit.prevent="addContact">
    <label
      >Name
      <input
        name="name"
        type="text"
        v-bind:placeholder="PLACEHOLDER.NAME"
        pattern="^[a-zA-Zа-яА-Я]+(([' -][a-zA-Zа-яА-Я ])?[a-zA-Zа-яА-Я]*)*$"
        title="Name may contain only letters, apostrophe, dash and spaces. For example Adrian, Jacob Mercer, Charles de Batz de Castelmore d'Artagnan"
      />
    </label>
    <label
      >Number
      <input
        name="phone"
        type="text"
        v-bind:placeholder="PLACEHOLDER.PHONE"
        pattern="\+?\d{1,4}?[-.\s]?\(?\d{1,3}?\)?[-.\s]?\d{1,4}[-.\s]?\d{1,4}[-.\s]?\d{1,9}"
        title="Phone number must be digits and can contain spaces, dashes, parentheses and can start with +"
      />
    </label>
    <SubmitBtn type="submit">Add contact</SubmitBtn>
  </form>
</template>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  flex-wrap: wrap;
  justify-content: flex-start;
}
label {
  font-weight: 500;
  margin-bottom: 12px;
}
input {
  padding: 4px 8px;
  border-radius: 8px;
  margin-left: 8px;
}
button {
  padding: 4px 8px;
  border-radius: 8px;
  background-color: transparent;
  transition: background-color 250ms cubic-bezier(0.47, 0, 0.745, 0.715);
  cursor: pointer;
}
button:hover {
  background-color: aqua;
}
</style>
