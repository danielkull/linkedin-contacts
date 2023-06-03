<template>
  <ContactsHeader :pendingInvitation="pendingInvitation" />
  <ContactsList />
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
    };
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
