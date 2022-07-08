<template>

  <div id="app">

    <!-- Here the header component -->
    <header>
      <PageHeader/>
    </header>

    <!-- Here the main section -->
    <main>
      <!-- Here the albums list component -->
      <AlbumsList/>

    </main>

    
  </div>

</template>

<script>

  import PageHeader from './components/PageHeader.vue';
  import AlbumsList from './components/AlbumsList.vue';

  export default {
    name: 'App',
    components: {
      PageHeader,
      AlbumsList
    }
  }

</script>

<style lang="scss">

</style>
