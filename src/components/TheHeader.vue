<script>
import { store } from "../store";
export default {
    data() {
        return {
            filteredMovies: [],
            store,

        }


    },
    methods: {




    }



}
</script>


<template>
    <div class="bg-danger">
        <div class="container">
            <div class="nav d-flex justify-content-between">
                <h1>Boolflix</h1>
                <div class="input-group input-group-sm mb-3">
                    <span class="input-group-text" id="inputGroup-sizing-sm">Search Movies</span>
                    <input type="text" class="form-control" aria-label="Sizing example input"
                        aria-describedby="inputGroup-sizing-sm" v-model="store.searchMovies">
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.nav {

    height: 80px;
    padding: 10px;

}

.input-group {
    height: 50px;
    width: 300px;
}
</style>