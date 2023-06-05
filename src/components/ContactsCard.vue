<template>
  <article class="contact-card">
    <div class="card__background-img">
      <img :src="backgroundImage" alt="" />
      <img class="card__profile-picture" :src="contactData.picture" alt="" />
    </div>
    <button
      @click.prevent="$emit('removeContact', index)"
      class="card__remove-btn"
    ></button>

    <section class="card__profile-data">
      <h3 class="profile__full-name">{{ profilFullName }}</h3>
      <p class="profile__profession">
        {{ contactData.title }}
      </p>
      <p class="profile__connections">
        🔗 {{ contactData.mutualConnections }} mutual connections
      </p>
      <p>{{ contactData.index }}</p>
    </section>
    <button @click="contactStatusHandler" class="toggle-connection-btn">
      {{ contactStatus }}
    </button>
  </article>
</template>

<script>
export default {
  data() {
    return {
      contactStatus: "Connect",
    };
  },
  props: ["contact-data", "index"],
  emits: ["updateInvitations", "removeContact"],
  computed: {
    profilFullName() {
      const profilName = this.contactData.name;
      return profilName.first + " " + profilName.last;
    },
    backgroundImage() {
      // return this.fixImagePath(this.contactData.backgroundImage);
      const urlPath = this.contactData.backgroundImage;
      let newValue = Math.floor(Math.random() * 100 + 300);
      const modifUrlPath = urlPath.replace("300", newValue);
      return modifUrlPath.replace("random", "featured");
    },
  },
  methods: {
    contactStatusHandler() {
      if (this.contactStatus === "Connect") {
        this.contactStatus = "Pending";
        this.$emit("updateInvitations", 1);
      } else {
        this.contactStatus = "Connect";
        this.$emit("updateInvitations", -1);
      }
    },
  },
};
</script>

<style>
.contact-card {
  display: flex;
  flex-direction: column;
  width: 10rem;
  height: 14rem;
  border: lightgray 1px solid;
  border-radius: 0.5rem;
  position: relative;
}

/* Start: Remove Card Button */
.card__remove-btn {
  position: absolute;
  top: 0.2rem;
  right: 0.2rem;
  padding: 1em;
  border: 2px solid white;
  border-radius: 50%;
  background: rgba(0, 0, 0, 0.7);
}

.card__remove-btn::after {
  content: "";
  position: absolute;
  top: 0%;
  left: 0%;
  translate: 50% 50%;
  background: rgba(255, 255, 255, 0.7);
  padding: 0.5rem;
  clip-path: polygon(
    10% 0%,
    0% 10%,
    40% 50%,
    0% 90%,
    10% 100%,
    50% 60%,
    90% 100%,
    100% 90%,
    60% 50%,
    100% 10%,
    90% 0%,
    50% 40%
  );
}

.card__remove-btn:hover {
  background: rgba(0, 0, 0, 1);
}
.card__remove-btn:hover.card__remove-btn::after {
  background: rgba(255, 255, 255, 1);
}

.card__remove-btn:active {
  scale: 1.05;
}

/* End: Remove Card Button */

.card__profile-data > h3 {
  font-size: 1rem;
}

.profile__profession {
  opacity: 0.9;
  margin-top: 0.2rem;
  font-size: 0.8rem;
}

.profile__connections {
  font-size: 0.6rem;
  margin-bottom: 1rem;
}

.card__background-img {
  height: 25%;
  overflow: hidden;
  border-radius: 0.5rem 0.5rem 0 0;
  margin-bottom: 3rem;
  background: radial-gradient(
      circle at 30% 60%,
      rgb(137, 168, 173) 63%,
      rgba(0, 0, 0, 0) 64%
    ),
    radial-gradient(
      circle at 170% 30%,
      rgb(137, 168, 173) 43%,
      rgba(0, 0, 0, 0) 44%
    ),
    rgb(212, 243, 248);
  background-repeat: no-repeat;
  background-size: cover;
}

.card__background-img img {
  translate: 0% -25%;
  object-fit: cover;
}

.card__profile-picture {
  width: 50%;
  position: absolute;
  top: 15%;
  left: 25%;
  clip-path: circle();
  /* scale: 1; */
}

.toggle-connection-btn {
  width: 90%;
  background-color: white;
  color: dodgerblue;
  font-weight: bold;
  border: 1px solid dodgerblue;
  border-radius: 1rem;
  padding-block: 0.3em;
  margin: auto;
}

.toggle-connection-btn:hover {
  background-color: dodgerblue;
  color: white;
}

.toggle-connection-btn:active {
  scale: 1.02;
  box-shadow: 1px 1px 2px darkcyan;
}
</style>
