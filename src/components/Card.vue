<script>
import LangFlag from 'vue-lang-code-flags';
export default {
    components: {
        LangFlag,
    },

    props: {
        movie: Object,
        required: true,



    },
    data() {
        return {

        }
    },


    methods: {
        getUrlImg(posterPath) {
            return `https://image.tmdb.org/t/p/w342${posterPath}`;
        },
        getVote(originalVote) {
            return Math.round(originalVote / 2);
        }
    },

}

</script>


<template>
    <div class="card-intera">

        <div class="my-card">
            <img :src="getUrlImg(movie.poster_path)" alt="">
            <div class="info-container">
                <h5 class="card-title" v-if="movie.title !== movie.original_title">Titolo Originale: {{
                    movie.title }}</h5>
                <h5 class="card-title" v-if="movie.original_title">Titolo: {{ movie.original_title }}</h5>
                <h5 class="card-title" v-if="movie.original_name">Serie Tv {{ movie.original_name }}</h5>

                <div v-for="star in 5" class="d-inline-flex">
                    <i v-if="star <= getVote(movie.vote_average)" class="fa-solid fa-star"></i>
                    <i v-else class="fa-regular fa-star"></i>
                </div>
                <p class="card-text">{{ movie.overview }}</p>
                <lang-flag :iso="movie.original_language" class="flag" />


            </div>
        </div>
    </div>
</template>


<style lang="scss" scoped>
.card-intera {
    position: relative;


    .my-card {
        display: inline-flex;

    }

    .info-container {
        padding: 1rem;
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        display: none;
        background-color: rgba(0, 0, 0, 0.555);
        color: white;
        width: 342px;

        h5 {
            font-size: 1rem;

        }

        p {
            font-size: .8rem;
        }

        i {
            color: goldenrod;
        }


    }

    .flag {
        width: 30px;
        height: 30px;
    }

}


.card-intera:hover .info-container {
    display: block;
}
</style>