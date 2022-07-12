<template>
    <div>
        <SearchBar @userSearch="userInputs" />
        <button @click="apiCall()">Search</button>
        <FilmCard :films="filmArray"/>
    </div>
</template>

<script>
import SearchBar from './SearchBar.vue'
import FilmCard from './FilmCard.vue'
import axios from 'axios'

export default {
    name: "MainComponent",
    components: {
        SearchBar,
        FilmCard
    },
    data() {
        return {
            url: 'https://api.themoviedb.org/3/search/movie?api_key=1a9d4ad303208935b21b8e064d453ab7&language=it-IT&query=',
            filmArray: null
        }
    },
    methods: {
        userInputs(words) {
            this.url = `https://api.themoviedb.org/3/search/movie?api_key=1a9d4ad303208935b21b8e064d453ab7&language=it-IT&query=${words}`
            // console.log(this.filmArray)
        },

        apiCall () {
            axios.get(this.url).then(response => {
                this.filmArray = response.data.results
                console.log(this.filmArray)
                
            })
        }
    },

}
</script>

<style lang="scss">
    
</style>