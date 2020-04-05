<template>
  <div class="show-film-details">
      <h1>{{ film.title }} ({{ film.release_date }})</h1>
      <h2 v-if="film.producer===film.director">Directed and produced by {{ film.producer }}</h2>
      <h2 v-else>Directed by {{ film.director }}, produced by {{ film.producer }}</h2>
      <p>{{ film.description }}</p>
      <p>Rotten Tomatoes: {{film.rt_score}}% {{ tomatometer }}</p>
  </div>
</template>

<script>
import { eventBus } from '../main.js';
export default {
    data() {
        return {
            film: null
        }
    },
    computed: {
        tomatometer() {
            if (this.film.rt_score >= 75){
                return "Certified Fresh"
            } else if (75 > this.film.rt_score >= 60) {
                return "Fresh"
            } else {
                return "Rotten"
            }
        }
    },
    mounted(){
        eventBus.$on('film-selected', (film) => {
            this.film = film;
        })
    }
}
</script>

<style>
    .show-film-details{
        border: 3px solid black;
        margin-top: 5px;
        margin-bottom: 5px;
        padding: 20px;
    }
</style>