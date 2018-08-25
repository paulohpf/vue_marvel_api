<template>
  <div id="app">
    <Title/>
    <Search @submit="searchComics"/>
    <List v-bind:items="results"/>
  </div>
</template>

<script>
  import Title from './components/Title';
  import Search from './components/Search';
  import List from './components/List'
  import axios from 'axios';

  export default {
    name: 'app',

    data() {
      return {
        results: []
      }
    },

    methods: {
      searchComics(text) {
        let search = (text) ? '&titleStartsWith=' + text : '';

        axios
        .get('https://gateway.marvel.com/v1/public/comics?format=comic&startYear=2018&formatType=comic&orderBy=modified&apikey=4c4180c92047d125cd72cbd256e62f57&ts=1533790666&hash=daff9eb8c8be71dd37410b6d9bac0c09&limit=12' + search)
        .then(res => {
          const r = res.data.data.results;

          this.results = r;
        });
      }
    },

    mounted() {
      this.searchComics();
    },

    components: {
      Title,
      Search,
      List
    }
  }
</script>

<style>

@import url('https://fonts.googleapis.com/css?family=Marvel:400,700');

body {
  padding: 0;
  margin: 0;
}

* {
  font-family: 'Marvel', sans-serif;
  box-sizing: border-box;
}

#app {
  padding: 0 20px;
}

</style>
