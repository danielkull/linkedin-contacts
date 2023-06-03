<template>
  <article class="contact-card">
    <div class="card__background-img">
      <img src="https://source.unsplash.com/featured/300x300" alt="" />
      <img
        class="card__profile-picture"
        src="https://randomuser.me/api/portraits/women/54.jpg"
        alt=""
      />
    </div>

    <section class="card__profile-data">
      <h3 class="profile__full-name">Dr. Guido de Melo</h3>
      <p class="profile__profession">
        Senior Manager bei BearingPoint Public...
      </p>
      <p class="profile__connections">🔗 2 mutual connections</p>
    </section>
    <button class="toggle-connection-btn">Connect</button>
  </article>
</template>

<script>
export default {};
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
</style>
