<template>
  <div class="choose-film-form">
    <h1>Select a Film</h1>
    <form>
      <select v-model="selectedFilm" v-on:change="handleSelectFilm" id="select-film">
        <option selected disabled value="">Select a film...</option>
        <option v-for="(film, index) in films" :key="index" :value="film">{{ film.title }}</option>
      </select>
    </form>
  </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  data() {
    return {
      selectedFilm: {}
    }
  },
  props: ['films'],
  methods: {
    handleSelectFilm() {
      eventBus.$emit('film-selected', this.selectedFilm)
    }
  }

}
</script>

<style>
  .choose-film-form {
    border: 3px solid black;
        margin-top: 5px;
        margin-bottom: 5px;
        padding: 20px;
  }
</style>