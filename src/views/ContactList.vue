<template>
    <div>
      <h1>Contact Book</h1>
      <input v-model="searchQuery" placeholder="Search by name..." />
      <ul>
        <li v-for="contact in filteredContacts" :key="contact.id">
          <router-link :to="'/contact/' + contact.id">{{ contact.firstName }} {{ contact.lastName }}</router-link>
        </li>
      </ul>
      <router-link to="/new">Add New Contact</router-link>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        searchQuery: '',
        contacts: JSON.parse(localStorage.getItem('contacts')) || []
      };
    },
    computed: {
      filteredContacts() {
        return this.contacts
          .filter(contact =>
            (contact.firstName + ' ' + contact.lastName)
              .toLowerCase()
              .includes(this.searchQuery.toLowerCase())
          )
          .sort((a, b) => a.lastName.localeCompare(b.lastName));
      }
    }
  };
  </script>
  