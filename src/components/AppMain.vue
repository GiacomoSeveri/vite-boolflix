<script>
import { store } from './data/store'
export default {
    name: 'AppMain',
    data() {
        return {
            store,
            imgSize: 'https://image.tmdb.org/t/p/w342/'
        }
    },

}
</script>

<template>
    <div class="custom-bgc pt-5">
        <h1 class="ms-2 text-danger">FILM</h1>
        <ul class="row row-cols-3 mx-0">
            <li class="my-3" v-for="movie in store.movies" :key="movie.id">
                <h3 class="text-light">{{ movie.title }}</h3>
                <p class="text-light">{{ movie.original_title }}</p>
                <img :src="imgSize + movie.poster_path" :alt="movie.title">
                <div class="d-flex justify-content-around">
                    <span class="text-light">{{ movie.original_language }}</span>
                    <span class="text-light">{{ movie.vote_average }}</span>
                </div>
            </li>
        </ul>

        <h1 class="mt-5 ms-2 text-danger">SERIE TV</h1>
        <ul class="row row-cols-3 mx-0 my-2">
            <li class="my-3" v-for="serie in store.series" :key="serie.id">
                <h3 class="text-light">{{ serie.name }}</h3>
                <p class="text-light">{{ serie.original_name }}</p>
                <img :src="imgSize + serie.poster_path" :alt="serie.name">
                <div class="d-flex justify-content-around">
                    <span class="text-light">{{ serie.original_language }}</span>
                    <span class="text-light">{{ serie.vote_average }}</span>
                </div>
            </li>
        </ul>
    </div>
</template>

<style scoped>
ul {
    list-style-type: none;
}

.custom-bgc {
    background-color: #434343;
    height: auto;
}
</style>