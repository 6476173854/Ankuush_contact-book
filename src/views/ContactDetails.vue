<template>
    <div>
      <h1>{{ contact.firstName }} {{ contact.lastName }}</h1>
      <p>Email: {{ contact.email }}</p>
      <p>Phone: {{ contact.phone }}</p>
      <router-link :to="'/edit/' + contact.id">Edit Contact</router-link>
      <button @click="deleteContact">Delete Contact</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        contact: {}
      };
    },
    created() {
      const id = this.$route.params.id;
      this.contact = JSON.parse(localStorage.getItem('contacts')).find(c => c.id === id);
    },
    methods: {
      deleteContact() {
        const contacts = JSON.parse(localStorage.getItem('contacts'));
        const updatedContacts = contacts.filter(contact => contact.id !== this.contact.id);
        localStorage.setItem('contacts', JSON.stringify(updatedContacts));
        this.$router.push('/');
      }
    }
  };
  </script>
  