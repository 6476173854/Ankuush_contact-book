<template>
  <div>
    <h1>Add New Contact</h1>
    <form @submit.prevent="addContact">
      <input v-model="firstName" placeholder="First Name" required />
      <input v-model="lastName" placeholder="Last Name" required />
      <input v-model="email" type="email" placeholder="Email" required />
      <input v-model="phone" placeholder="Phone" />
      <button type="submit">Add Contact</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      firstName: '',
      lastName: '',
      email: '',
      phone: ''
    };
  },
  methods: {
    addContact() {
      const contacts = JSON.parse(localStorage.getItem('contacts')) || [];
      const newContact = {
        id: Date.now().toString(),
        firstName: this.firstName,
        lastName: this.lastName,
        email: this.email,
        phone: this.phone
      };
      contacts.push(newContact);
      localStorage.setItem('contacts', JSON.stringify(contacts));
      this.$router.push('/contact/' + newContact.id);
    }
  }
};
</script>
