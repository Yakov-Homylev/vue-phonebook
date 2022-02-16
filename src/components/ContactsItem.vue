<template>
  <li class="card">
    <p>{{ name }}</p>
    <p>{{ phone }}</p>
    <SubmitBtn @click="deleteContact">Delete</SubmitBtn>
  </li>
</template>

<script>
import { ref } from "@vue/reactivity";
import SubmitBtn from "./UI/SubmitBtn.vue";
import axios from "axios";
import { inject } from "@vue/runtime-core";

export default {
  components: { SubmitBtn },
  props: ["contact"],
  setup(props) {
    const name = ref(props.contact.name);
    const phone = ref(props.contact.phone);

    const contacts = inject("contacts");

    const deleteContact = () => {
      axios.delete(
        `https://61e92eaa7bc0550017bc60f7.mockapi.io/contacts/${props.contact.id}`
      );

      contacts.value = contacts.value.filter(
        (el) => el.id !== props.contact.id
      );
    };

    return { name, phone, deleteContact, contacts };
  },
};
</script>

<style scoped>
p {
  margin: 0;
}
.card {
  padding: 8px;
  gap: 12px;
  border-radius: 12px;
  box-shadow: 0px 1px 3px 0px rgba(0, 0, 0, 0.2),
    0px 1px 1px 0px rgba(0, 0, 0, 0.14), 0px 2px 1px -1px rgba(0, 0, 0, 0.12);
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
