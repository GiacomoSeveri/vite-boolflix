<script>
import { store } from './data/store'
export default {
    name: 'filmCard',
    data() {
        return {
            store,
            imgTunnel: 'https://image.tmdb.org/t/p/w342/'
        }
    },
    methods: {
        voteFilm(i) {
            return Math.ceil(parseInt(this.store.movies[i].vote_average) / 2)
        },
    }
}
</script>

<template>
    <h1 v-show="store.movies.length >= 1" class="mt-3 mb-5 text-danger text-center" type="button">FILM</h1>
    <div class="container">
        <ul class="row row-cols-lg-4  d-flex justify-content-start">
            <li class="my-3 d-flex justify-content-center m-0" v-for="(movie, i) in store.movies" :key="movie.id">
                <figure>
                    <img class="m-0 cover" :src="imgTunnel + movie.poster_path" :alt="movie.title">
                    <div class="caption">
                        <h3 class="text-danger-emphasis">{{ movie.title }}</h3>
                        <h5 class="text-danger">{{ movie.original_title }}</h5>
                        <span class="text-light">{{ movie.overview }}</span>
                        <div class="d-flex justify-content-around mt-3">
                            <img class="flag text-light" :src="`img/${movie.original_language}.png`"
                                :alt="movie.original_language">
                            <i v-for="n in 5" :class="n <= voteFilm(i) ? 'fa-solid' : 'fa-regular'"
                                class="fa-star text-warning"></i>
                        </div>
                    </div>
                </figure>
            </li>
        </ul>
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