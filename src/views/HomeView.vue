<template>
  <ContactsHeader :pendingInvitation="pendingInvitation" />
  <ContactsList
    :contacts="contacts"
    @update-invitations="(n) => this.updatePendingInvitations(n)"
    @remove-contact="(index) => this.removeContact(index)"
  />
</template>

<script>
import ContactsHeader from "@/components/ContactsHeader.vue";
import ContactsList from "@/components/ContactsList.vue";
export default {
  name: "HomeView",
  components: { ContactsHeader, ContactsList },
  data() {
    return {
      pendingInvitation: 0,
      contacts: [],
    };
  },
  methods: {
    updatePendingInvitations(value) {
      this.pendingInvitation += value;
    },
    removeContact(i) {
      this.contacts = this.contacts.filter((item, index) => {
        return index !== i;
      });
      this.fetchNewContact();
    },
    async fetchNewContact() {
      const response = await fetch(
        "https://dummy-apis.netlify.app/api/contact-suggestions"
      );
      const newContact = await response.json();
      this.contacts.push(newContact[0]);
    },
  },
  async created() {
    const response = await fetch(
      "https://dummy-apis.netlify.app/api/contact-suggestions?count=8"
    );
    this.contacts = await response.json();
  },
};
</script>

<style>
body {
  display: grid;
  align-content: center;
  background-color: #f4f4f4;
}
</style>
