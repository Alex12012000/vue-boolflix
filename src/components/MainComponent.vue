<template>
    <div>
        <SearchBar @userSearch="userInputs" />
        <button @click="apiCall(), apiCallTv()" >Search</button>
        <FilmCard :films="filmArray"/>
        <ShowCard :tvShow="tvShowArray"/>
    </div>
</template>

<script>
import SearchBar from './SearchBar.vue'
import FilmCard from './FilmCard.vue'
import ShowCard from './ShowCard.vue'
import axios from 'axios'

export default {
    name: "MainComponent",
    components: {
        SearchBar,
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
    },

}
</script>

<style lang="scss">
    
</style>