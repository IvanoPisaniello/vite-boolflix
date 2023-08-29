<script>
export default {
    props: {
        movies: Object,
        required: true,
    },
    data() {
        return {

        }
    },


    methods: {

    }

}

</script>


<template>
    <div class="card" style="width: 18rem;" v-for="movie in  movies">

        <div class="card-body">
            <h5 class="card-title">{{ movie.original_title }}</h5>
            <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's
                content.</p>
            <a href="#" class="btn btn-primary">Go somewhere</a>
        </div>
    </div>
</template>


<style lang="scss" scoped></style>