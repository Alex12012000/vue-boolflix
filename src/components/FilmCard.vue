<template>
    <div>
        <h2>Film</h2>
        <div v-for="film, index in films" :key="index">
            <img v-if="film.backdrop_path !== null" :src="posterImg(film.backdrop_path)" alt="">
            <img v-else src="https://www.salonlfc.com/wp-content/uploads/2018/01/image-not-found-scaled-1150x647.png" alt="">
            <h2>{{film.title}}</h2>
            <h3>{{film.original_title}}</h3>
            <img :src="justFlags(film.original_language)" alt="">
            <div class="stars">
                {{roundVote(film.vote_average)}}
                <i v-for="el, index in fullStarArray" :key="index" class="fa-solid fa-star"></i>
                <i v-for="el, index in emptyStar" :key="index"  class="fa-regular fa-star"></i>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'FilmCard',
    props: {
        films: Array,
    },
    data() {
        return {
            fullStarArray: null,
            emptyStar: null
        }
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
            if (nation === 'ko') {
                nation = 'kr'
            }
            if (nation === 'zh') {
                nation === 'cn'
            }

            return `https://countryflagsapi.com/png/${nation}`
        },
        
        posterImg(img) {
            return `https://image.tmdb.org/t/p/w780/${img}`
        },

        roundVote(vote) {
            
            const finalVote = (vote / 2).toFixed(0)
            if ( finalVote === '1') {
                this.fullStarArray = [1]
                this.emptyStar = [1, 2, 3, 4]
            }
            if ( finalVote === '2') {
                this.fullStarArray = [1, 2,]
                this.emptyStar = [1, 2, 3]
            }
            if ( finalVote === '3') {
                this.fullStarArray = [1, 2, 3]
                this.emptyStar = [1, 2]
            }
            if ( finalVote === '4') {
                this.fullStarArray = [1, 2, 3, 4]
                this.emptyStar = [1]
            }
            if ( finalVote === '5') {
                this.fullStarArray = [1, 2, 3, 4, 5]
                this.emptyStar = []
            }
        }
    },
}
</script>
<style lang="">
    
</style>