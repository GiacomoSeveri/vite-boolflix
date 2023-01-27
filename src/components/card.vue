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
}
</script>

<template>
    <div class="custom-bgc pt-5">
        <h1 class="ms-2 text-danger">FILM</h1>
        <div class="container">
            <ul class="hover-data2 row row-cols-4 d-flex justify-content-start">
                <li class="my-3 d-flex justify-content-center m-0" v-for="movie in store.movies" :key="movie.id">
                    <figure>
                        <img class="m-0 cover" :src="imgTunnel + movie.poster_path" :alt="movie.title">
                        <div class="caption">
                            <h3 class="text-danger">{{ movie.title }}</h3>
                            <h5 class="text-light">{{ movie.original_title }}</h5>
                            <span class="text-light mb-4">{{ movie.overview }}</span>
                            <div class="d-flex justify-content-around">
                                <span class="text-light">{{ movie.original_language }}</span>
                                <span class="text-warning">{{ movie.vote_average }}</span>
                            </div>
                        </div>
                    </figure>
                </li>
            </ul>
        </div>

        <h1 class="ms-2 text-danger">SERIE TV</h1>
        <div class="container">
            <ul class="hover-data2 row row-cols-4 d-flex justify-content-start">
                <li class="my-3 d-flex justify-content-center m-0" v-for="serie in store.series" :key="serie.id">
                    <figure>
                        <img class="m-0 cover" :src="imgTunnel + serie.poster_path" :alt="serie.name">
                        <div class="caption">
                            <h3 class="text-danger">{{ serie.name }}</h3>
                            <h5 class="text-light">{{ serie.original_name }}</h5>
                            <span class="text-light pb-4">{{ serie.overview }}</span>
                            <div class="d-flex justify-content-around">
                                <span class="text-light">{{ serie.original_language }}</span>
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
                border: solid 1px rgb(155, 51, 51);
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


}
</style>