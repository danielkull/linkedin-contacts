<template>
  <main class="contacts__main">
    <sections class="contacts--list__header">
      <h2 class="contacts-intro-text">
        People you may know in Greater Nuremberg Metropolitan Area
      </h2>
      <button @click.prevent class="btn-contact-change-view">See all</button>
    </sections>
    <sections class="contacts--list__main">
      <ContactsCard
        v-for="(contact, index) in contacts"
        :key="index"
        :contact-data="contact"
        :index="index"
        @update-invitations="(n) => $emit('updateInvitations', n)"
        @remove-contact="(index) => $emit('removeContact', index)"
      >
      </ContactsCard>
    </sections>
  </main>
</template>

<script>
import ContactsCard from "@/components/ContactsCard.vue";
export default {
  emits: ["updateInvitations", "removeContact"],
  components: {
    ContactsCard,
  },
  props: ["contacts"],
};
</script>

<style>
.contacts__main {
  width: min-content;
  margin-top: 1rem;
  margin-inline: auto;
  border: 1px solid rgb(187, 186, 186);
  background-color: #fefefe;
  padding: 0.5em 1em;
  border-radius: 0.5rem;
}

.contacts--list__header {
  font-size: 1rem;
  display: flex;
}

.contacts-intro-text {
  font-size: inherit;
  font-weight: normal;
}

.btn-contact-change-view {
  margin-left: auto;
  border: none;
  background: none;
  font-weight: bold;
  opacity: 0.8;
}

.contacts--list__main {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 0.5rem;
}
</style>
