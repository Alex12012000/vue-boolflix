<template>
  <div id="app">
    <HeaderComponent @userSearch="userInputs" @filmCall="apiCall" @tvCall="apiCallTv"/>
    
    <main>
      <FilmCard :films="filmArray"/>
      <ShowCard :tvShow="tvShowArray"/>
    </main>

  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import HeaderComponent from './components/HeaderComponent.vue'
import FilmCard from './components/FilmCard.vue'
import ShowCard from './components/ShowCard.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    FilmCard,
    ShowCard

  },
  data() {
        return {
            url: 'https://api.themoviedb.org/3/search/movie?api_key=1a9d4ad303208935b21b8e064d453ab7&language=it-IT&query=',
            tvUrl: 'https://api.themoviedb.org/3/search/tv?api_key=1a9d4ad303208935b21b8e064d453ab7&&language=it-IT&query=',
            filmArray: null,
            tvShowArray: null,
            
        }
    },
    methods: {
        userInputs(words) {
            this.url = `https://api.themoviedb.org/3/search/movie?api_key=1a9d4ad303208935b21b8e064d453ab7&language=it-IT&query=${words}`
            this.tvUrl = `https://api.themoviedb.org/3/search/tv?api_key=1a9d4ad303208935b21b8e064d453ab7&&language=it-IT&query=${words}`
        },
        apiCall () {
            axios.get(this.url).then(response => {
                this.filmArray = response.data.results
            })
        },
        apiCallTv () {
            axios.get(this.tvUrl).then(response => {
                this.tvShowArray = response.data.results
            })
        },

        topRatedFilm() {
          axios.get('https://api.themoviedb.org/3/movie/top_rated?api_key=1a9d4ad303208935b21b8e064d453ab7&language=it-IT&page=1').then(response => {
                this.filmArray = response.data.results
            })
        },

        topRatedShow() {
          axios.get('https://api.themoviedb.org/3/tv/top_rated?api_key=1a9d4ad303208935b21b8e064d453ab7&language=it-IT&page=1').then(response => {
                this.tvShowArray = response.data.results
            })
        }
    },
    mounted() {
      this.topRatedFilm()
      this.topRatedShow()
    },

}
</script>

<style lang="scss">
@import './style/common.scss'; 


</style>
