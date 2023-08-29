<script>

export default {
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
            return `https://image.tmdb.org/t/p/w200${posterPath}`;
        },
        getVote(originalVote) {
            return Math.round(originalVote / 2);
        }
    },

}

</script>


<template>
    <div class="">

        <div class="my-card">
            <img :src="getUrlImg(movie.poster_path)" alt="">
            <!-- <h5 class="card-title">{{ movie.original_title }}</h5>
            <h5 class="card-title">{{ movie.original_name }}</h5>
            <p class="card-text">{{ movie.overview }}</p>
            <div v-for="star in 5" class="d-flex">
                <i v-if="star <= getVote(movie.vote_average)" class="fa-solid fa-star"></i>
                <i v-else class="fa-regular fa-star"></i>
            </div> -->

        </div>
    </div>
</template>


<style lang="scss" scoped>
.my-card {
    display: flex;
}
</style>