<script>
import { store } from "../store";

export default {
    data() {
        return {
            filteredMovies: [],
            store,
            searchMovies: "",
            store,

        }


    },
    methods: {
        onEnter() {

            store.searchMovies = this.searchMovies
            console.log("funziona")
            this.searchMovies = "";
        }



    }



}
</script>


<template>
    <div class="bg-black">
        <div class="container">
            <div class="nav d-flex justify-content-between">
                <img src="../assets/Netflix-logo.wine.svg" class="logo-img" alt="">
                <div class="input-group input-group-sm mb-3">

                    <input type="text" class="form-control" aria-label="Sizing example input"
                        aria-describedby="inputGroup-sizing-sm" v-model="searchMovies" @keyup.enter="onEnter()">
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.nav {

    height: 80px;
    padding: 10px;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    background-color: rgba(0, 0, 0, 0.728);
    z-index: 3;

}

.input-group {
    height: 50px;
    width: 250px;
}

.logo-img {
    height: 60px;
    width: 300px;

}
</style>