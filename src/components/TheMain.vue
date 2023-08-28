<script>
import Card from "./Card.vue";
import axios from "axios";
import { store } from "../store";
export default {
    components: {
        Card,
    },

    data() {
        return {
            store,
            movies: [],
        }
    },

    methods: {

    },
    mounted() {

    },
    watch: {
        // filterMovies() {
        //     const url = `https://api.themoviedb.org/3/search/movie?api_key=b54d72c5e7b0cdfd35ea60e05ff5547b&query=${store.searchMovies}&language=it-IT`

        //     axios.get(url).then((response) => {

        //         this.movies = response.data.results;
        //         console.log(this.movies);

        //     })

        // }
        "store.searchMovies": function (searchMovies) {
            this.movies = [];
            const url = `https://api.themoviedb.org/3/search/movie?api_key=b54d72c5e7b0cdfd35ea60e05ff5547b&query=${store.searchMovies}&language=it-IT`

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
        <li v-for="movie in movies">
            {{ movie.title }}
        </li>
    </ul>
</template>

<style lang="scss" scoped></style>