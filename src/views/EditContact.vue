<template>
  <div>
    <h1>Edit Contact</h1>
    <form @submit.prevent="editContact">
      <input v-model="contact.firstName" placeholder="First Name" required />
      <input v-model="contact.lastName" placeholder="Last Name" required />
      <input v-model="contact.email" type="email" placeholder="Email" required />
      <input v-model="contact.phone" placeholder="Phone" />
      <button type="submit">Save Changes</button>
    </form>
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
    editContact() {
      const contacts = JSON.parse(localStorage.getItem('contacts'));
      const index = contacts.findIndex(c => c.id === this.contact.id);
      if (index !== -1) {
        contacts[index] = { ...this.contact };
        localStorage.setItem('contacts', JSON.stringify(contacts));
        this.$router.push('/contact/' + this.contact.id);
      }
    }
  }
};
</script>
