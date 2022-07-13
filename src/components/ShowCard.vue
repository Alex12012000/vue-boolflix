<template>
    <div class="container">
        <h2>Serie Tv</h2>
        <div class="card-container">
            <div v-for="show, index in tvShow" :key="index" class="show-card">
                <div class="poster">
                    <img v-if="show.backdrop_path !== null" :src="posterImg(show.backdrop_path)" alt="" class="poster-img">
                    <img v-else src="https://www.salonlfc.com/wp-content/uploads/2018/01/image-not-found-scaled-1150x647.png" alt="" class="poster-img">
                    <div class="show-info">
                        <div class="title flex">
                            <span>Titolo:</span>
                            <h3>{{show.name}}</h3>
                        </div>
                        <div class="orginal-title flex">
                            <span>Titolo originale:</span>
                            <h3>{{show.original_name}}</h3>
                        </div>
                        <div class="flag">
                            <img :src="justFlags(show.original_language)" alt="">
                        </div>
                        <div class="rating flex">
                            <span>Voto</span>
                            <div class="stars">
                                <i class="fa-solid fa-star" :class="{'full-star': num <= roundVote(show.vote_average)}" v-for="num in 5" :key="num"></i>
                            </div>
                        </div>

                        <div class="overview">
                            <span>Overview: </span>
                            <p>{{trimmedText(show.overview)}}..</p>
                        </div>
                    </div>
                </div>
                
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'ShowCard',
    props: {
        tvShow: Array,
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
            return finalVote
        },

        trimmedText(text) {
            return text.slice(0, 90)
        }
    },
}
</script>
<style lang="scss" scoped>
    h2 {
        color: white;
        text-align: center;
        margin: 30px 10px;
        text-transform: uppercase;
    }
    .card-container {
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;

        .show-card {
            width: calc((100% / 5) - 20px);
            color: white;

            .poster {
                height: 350px;
                margin: 10px 0;
                position: relative;
                border: 1px solid white;
                img {
                    height: 100%;
                    object-fit: cover;
                }
                .show-info {
                    padding: 20px;
                    position: absolute;
                    top: 0;
                    right: 0;
                    z-index: 10;
                    display: none;
                }

                span {
                    font-weight: 800;
                    margin-right: 2px;
                }
                h3 {
                    font-size: 16px;
                    font-weight: 300;
                }
                .flag {
                    width: 30px;
                    margin: 10px 0;
                }

            }
            
            .poster:hover .show-info {
                display: block;
            }

            .poster:hover .poster-img {
                display: none;
            }

            .poster:hover {
                background-color: black;
            }
        
        }
    }

    .flex {
        display: flex;
        flex-wrap: wrap;
    }

    .full-star {
        color: yellow;
    }
    
</style>