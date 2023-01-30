<script>
import { store } from './data/store'
export default {
    name: 'card',
    data() {
        return {
            store,
            imgTunnel: 'https://image.tmdb.org/t/p/w342/'
        }
    },
    computed: {
        vote() {
            return Math.ceil(this.store.movies.vote_average / 2)
        }
    }
}
</script>

<template>
    <div class="custom-bgc pt-5">
        <h1 v-show="store.movies.length >= 1" class="mb-5 text-danger text-center" type="button">FILM</h1>
        <div class="container">
            <ul class="row row-cols-lg-4  d-flex justify-content-start">
                <li class="my-3 d-flex justify-content-center m-0" v-for="movie in store.movies" :key="movie.id">
                    <figure>
                        <img class="m-0 cover" :src="imgTunnel + movie.poster_path" :alt="movie.title">
                        <div class="caption">
                            <h3 class="text-danger-emphasis">{{ movie.title }}</h3>
                            <h5 class="text-danger">{{ movie.original_title }}</h5>
                            <span class="text-light">{{ movie.overview }}</span>
                            <div class="d-flex justify-content-around mt-3">
                                <img class="flag text-light" :src="`img/${movie.original_language}.png`"
                                    :alt="movie.original_language">
                                <span class="text-warning">{{ vote }}</span>
                            </div>
                        </div>
                    </figure>
                </li>
            </ul>
        </div>

        <h1 v-show="store.series.length >= 1" class="my-5 text-danger text-center" type="button">SERIE TV</h1>
        <div class="container">
            <ul class="row row-cols-4 d-flex justify-content-start">
                <li class="my-3 d-flex justify-content-center m-0" v-for="serie in store.series" :key="serie.id">
                    <figure>
                        <img class="m-0 cover" :src="imgTunnel + serie.poster_path" :alt="serie.name">
                        <div class="caption">
                            <h3 class="text-danger-emphasis">{{ serie.name }}</h3>
                            <h5 class="text-danger">{{ serie.original_name }}</h5>
                            <span class="text-light">{{ serie.overview }}</span>
                            <div class="d-flex justify-content-around mt-3">
                                <img class="flag text-light" :src="`img/${serie.original_language}.png`"
                                    :alt="serie.original_language">
                                <span class="text-warning">{{ serie.vote_average }}</span>
                            </div>
                        </div>
                    </figure>
                </li>
            </ul>
        </div>
    </div>
</template>

<style lang="scss" scoped>
ul {
    list-style-type: none;

    li {

        figure {
            img {
                border: solid 1px #fff;
                width: 250px;
                height: 360px;
                cursor: pointer;
                position: relative;
            }

            .caption {
                position: relative;
                top: 0px;
                right: 0;
                display: none;
                width: 250px;
                height: 360px;
                border: solid 1px #fff;
                padding: 1rem;
                overflow-y: auto;
                cursor: pointer;
            }

            &:hover .cover {
                display: none;
            }

            &:hover .caption {
                display: block;
                background-color: #000000;
            }
        }
    }

    .flag {
        width: 35px;
        height: 20px;
    }
}
</style>