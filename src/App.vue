<template>

  <div id="app">

    <!-- Here the header component -->
    <header>
      <PageHeader :albumGenres="albumGenres" @selectGenre="setGenre"/>
    </header>

    <!-- Here the main section -->
    <main>
      <!-- Here the albums list component -->
      <AlbumsList :genreToShow="genreToShow" @genresInfo="getAllGenres"/>

    </main>

    
  </div>

</template>

<script>

  import PageHeader from './components/PageHeader.vue';
  import AlbumsList from './components/AlbumsList.vue';

  export default {
    name: 'App',
    components: { PageHeader, AlbumsList },
    data() {
      return {
        genreToShow: '',
        albumGenres: []
      }
    },
    methods: {
      setGenre(genre){
        this.genreToShow = genre;
      },
      getAllGenres(genres) {
        this.albumGenres = genres;
      }
    }
  }

</script>

<style lang="scss">

</style>
