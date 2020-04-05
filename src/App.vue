<template>
  <div>
    <h1>Ghibli Oeuvre</h1>
    <choose-film-form :films="films"></choose-film-form>
    <show-film-details></show-film-details>
  </div>
</template>

<script>
import ChooseFilmForm from './components/ChooseFilmForm';
import ShowFilmDetails from './components/ShowFilmDetails';

export default {
  data() {
    return {
      films: []
    }
  },
  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then( response => response.json() )
    .then( films => this.films = films )
  },
  components: {
    'choose-film-form': ChooseFilmForm,
    'show-film-details': ShowFilmDetails
  }

}
</script>

<style>

</style>