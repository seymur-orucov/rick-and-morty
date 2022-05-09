<template>
  <article class="character">
    <div class="character__image">
      <img :src="character.image" :alt="character.name" />
    </div>
    <div class="character__info">
      <h2 class="character__info-name">{{ character.name }}</h2>
      <span class="character__info-status"
        >{{ character.status }} - {{ character.species }}</span
      >
      <span class="character__info-title">Last known location:</span>
      <span class="character__info-subtitle">{{ character.origin.name }}</span>
      <span class="character__info-title">First seen in:</span>
      <span class="character__info-subtitle">{{
        character.location.name
      }}</span>
    </div>
  </article>
</template>

<script>
export default {
  props: {
    character: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
.character {
  display: flex;
  background-color: #3c3e44;
  border-radius: 0.5em;
  overflow: hidden;
  width: 600px;
  height: 250px;
  margin: 2em;

  &__image {
    width: 250px;
    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      background-position: center;
    }
  }
  &__info {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 1.5em;
    text-align: left;
    &-name {
      font-size: 2.6rem;
      color: #ffffff;
      margin: 0;
    }
    &-status {
      display: block;
      font-size: 1.6rem;
      color: #ffffff;
      font-weight: 600;
      margin: 1em 0 1.2em 0;
    }
    &-title {
      display: block;
      font-size: 1.4rem;
      font-weight: 600;
      color: rgb(158, 158, 158);
      margin: 1em 0 0.5em 0;
    }
    &-subtitle {
      font-size: 1.8rem;
      color: #ffffff;
    }
  }
}
</style>
