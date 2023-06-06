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
    addContectStatus(arr) {
      arr.forEach((contact) => {
        contact.contactStatus = "Connect";
      });
    },
    async fetchNewContact() {
      const response = await fetch(
        "https://dummy-apis.netlify.app/api/contact-suggestions"
      );
      const newContact = await response.json();
      // newContact[0].contactStatus = "Connect";
      this.contacts.push(newContact[0]);
      this.addContectStatus(newContact);
    },
  },
  async created() {
    const response = await fetch(
      "https://dummy-apis.netlify.app/api/contact-suggestions?count=8"
    );
    this.contacts = await response.json();
    this.addContectStatus(this.contacts);
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
