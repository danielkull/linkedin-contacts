<template>
  <header class="contacts__header">
    <h3 class="pending-inventions-text">{{ openInvitations }}</h3>
    <button @click.prevent class="btn-mange-invites">Manage</button>
  </header>
</template>

<script>
export default {
  props: {
    pendingInvitation: {
      type: Number,
      required: true,
      default: 0,
    },
  },
  computed: {
    openInvitations() {
      if (!this.pendingInvitation) {
        return "No pending invitations";
      } else if (this.pendingInvitation === 1) {
        return `${this.pendingInvitation} pending invitation`;
      } else {
        return `${this.pendingInvitation} pending invitations`;
      }
    },
  },
};
</script>

<style scoped>
.contacts__header {
  font-size: 1rem;
  display: flex;
  margin: 0 auto;
  width: 90%;
  border-radius: 0.5rem;
  border: 1px solid rgb(187, 186, 186);
  background-color: #fefefe;
  padding: 0.5em 1em;
}

.pending-inventions-text,
.btn-mange-invites {
  display: inline-block;
}

.pending-inventions-text {
  font-size: inherit;
  font-weight: normal;
}

.btn-mange-invites {
  margin-left: auto;
  border: none;
  background: none;
  font-weight: bold;
  opacity: 0.8;
}
</style>
