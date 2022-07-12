<template>
    <div>
        <h2>Serie Tv</h2>
        <div v-for="show, index in tvShow" :key="index">
            <h2>{{show.name}}</h2>
            <h3>{{show.original_name}}</h3>
            <img :src="justFlags(show.original_language)" alt="">
            <h3>{{show.vote_average}}</h3>
        </div>
    </div>
</template>
<script>
export default {
    name: 'ShowCard',
    props: {
        tvShow: Array
    },
    methods: {
        justFlags(nation) {
            if(nation === 'en') {
                nation = 'us'
            }
            if (nation === 'hi') {
                nation = 'in'
            }
            if (nation === 'ja') {
                nation = 'jp'
            }
            if (nation === 'cs') {
                nation = 'cz'
            }

            return `https://countryflagsapi.com/png/${nation}`
        }
    },
}
</script>
<style lang="">
    
</style>