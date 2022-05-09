<template>
  <div class="character-list">
    <Character
      v-for="(character, index) in characters"
      :key="index"
      :character="character"
    />
    <a href="javascript:void(0);" class="load-more" @click="fetchCharacters"
      >Load More</a
    >
  </div>
</template>

<script>
import Character from "@/components/Character.vue";

export default {
  components: {
    Character,
  },
  data: () => ({
    characters: [],
    currentPage: 1,
  }),
  mounted() {
    this.fetchCharacters();
  },
  methods: {
    fetchCharacters() {
      this.axios
        .get("https://rickandmortyapi.com/api/character", {
          params: { page: this.currentPage },
        })
        .then((response) => {
          this.characters = [...this.characters, ...response.data.results];
          console.log(this.characters);
          this.currentPage++;
        });
    },
  },
};
</script>

<style lang="sass" scoped>
.character-list
  display: flex
  flex-wrap: wrap
  justify-content: center
.load-more
  margin-top: 1.5em
  color: rgb(255 255 255)
  font-size: 2rem
  font-weight: 700
  border: 2px solid #ff9800
  border-radius: 5px
  text-decoration: none
  padding: 0.6em 0.8em
  transition: ease-in-out 0.2s
  &:hover
    background-color: #ff9800
</style>
