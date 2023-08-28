<script>
import Card from "./Card.vue";
import axios from "axios";
import { store } from "../store";
import { findFlagUrlByIso2Code } from "country-flags-svg";

export default {
    components: {
        Card,
    },

    data() {
        return {
            store,
            movies: [],
            searchMovies: "",

        }
    },

    methods: {

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
    <Card></Card>
    <ul>
        <li class="list-unstyled" v-for="movie in   movies  ">
            {{ movie.title }}
            <ul>
                <li class="list-unstyled">
                    <p class="d-block">{{ movie.original_title }} </p>
                    <p class="d-block">{{ movie.original_name }}</p>
                    <p class="d-block"> Lingua Originale: {{ movie.original_language }} </p>
                    <p>Voto: {{ movie.vote_average }}</p>
                </li>
            </ul>
        </li>
    </ul>
</template>

<style lang="scss" scoped>
.img-flag {
    height: 20px;
}
</style>