<template>
    <div>
        <div v-for="film, index in films" :key="index">
            <h2>{{film.title}}</h2>
            <h3>{{film.original_title}}</h3>
            <h3>{{film.original_language}}</h3>
            <h3>{{film.vote_average}}</h3>
        </div>
    </div>
</template>
<script>
export default {
    name: 'FilmCard',
    props: {
        films: Array
    }
}
</script>
<style lang="">
    
</style>