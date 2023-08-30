<script>
import Card from "./Card.vue";
import axios from "axios";
import { store } from "../store";
// import LangFlag from 'vue-lang-code-flags'

export default {
    components: {
        Card,
        // LangFlag,
    },

    data() {
        return {
            store,
            movies: [],
            searchMovies: "",
            urlImg: "",


        }
    },

    methods: {
        getUrlImg(posterPath) {
            return `https://image.tmdb.org/t/p/w92${posterPath}`;
        },
        getVote(originalVote) {
            return Math.round(originalVote / 2);
        }
    },
    mounted() {

    },


    watch: {

        "store.searchMovies": function (searchMovies) {
            this.movies = [];
            const url = `https://api.themoviedb.org/3/search/multi?api_key=b54d72c5e7b0cdfd35ea60e05ff5547b&query=${store.searchMovies}&language=it-IT`

            axios.get(url).then((response) => {

                this.movies = response.data.results;
                console.log(this.movies);


            })
        }
    }
}

</script>


<template>
    <div class="p-4">
        <div class="row card-container justify-content-center gap-1">
            <div class="p-0 m-0 colonna-card" v-for="movie in movies">
                <Card :key="movie.id" :overview="movie.overview" :vote="movie.vote_average" :movie="movie"
                    :name="movie.original_name" :language="movie.original_language" :title="movie.title" :src="movie.src"
                    :original="movie.original_title" />
            </div>
        </div>
    </div>
    <!-- <ul>
        <li class="list-unstyled" v-for="movie in   movies  ">
            {{ movie.title }}
            <ul>
                <li class="list-unstyled">
                    <p class="d-block">{{ movie.original_title }} </p>
                    <p class="d-block">{{ movie.original_name }}</p>
                    <lang-flag :iso="movie.original_language" />
                    <p>Voto: {{ getVote(movie.vote_average) }}</p>
                    <img :src="getUrlImg(movie.poster_path)" alt="">
                    <div v-for="star in 5" class="d-flex">
                        <i v-if="star <= getVote(movie.vote_average)" class="fa-solid fa-star"></i>
                        <i v-else class="fa-regular fa-star"></i>
                    </div>


                </li>
            </ul>
        </li>
    </ul> -->
</template>

<style lang="scss" scoped>
.img-flag {
    height: 20px;

}

.colonna-card {
    width: 342px;

}
</style>