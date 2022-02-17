<script>
import Title from "./components/Title.vue";
import ContactsForm from "./components/ContactsForm.vue";
import Filter from "./components/Filter.vue";
import ContactsList from "./components/ContactsList.vue";
import ContactsItem from "./components/ContactsItem.vue";
export default {
  components: [Title, ContactsForm, Filter, ContactsList, ContactsItem],
};
</script>

<script setup>
import axios from "axios";
import { ref, provide, reactive, onMounted, watch } from "vue";
const titleName = "Phonebook";

const contacts = ref([]);

onMounted(async () => {
  const response = await axios.get(
    "https://61e92eaa7bc0550017bc60f7.mockapi.io/contacts"
  );
  contacts.value = [...response.data];
});

const addContact = (e) => {
  const newContact = {
    name: e.target.name.value,
    phone: e.target.phone.value,
  };

  contacts.value = [newContact, ...contacts.value];

  axios.post(
    "https://61e92eaa7bc0550017bc60f7.mockapi.io/contacts",
    newContact
  );

  e.target.reset();
};

const visibleContacts = reactive(contacts);
const filter = ref("");

watch(filter, () => {
  visibleContacts.value = [...contacts.value].filter((contact) =>
    contact.name.toLowerCase().includes(filter.value)
  );
});

provide("contacts", contacts);
provide("addContact", addContact);
provide("visibleContacts", visibleContacts);
provide("filter", filter);
</script>

<template>
  <div class="wrapper">
    <Title v-bind:text="titleName" />
    <ContactsForm />
    <Filter />
    <ContactsList v-if="visibleContacts.length > 0">
      <ContactsItem
        v-for="contact in visibleContacts"
        v-bind:key="contact.id"
        :contact="contact"
      />
    </ContactsList>
    <p v-else>Contacts list is clear</p>
  </div>
</template>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 12px;
}
</style>
