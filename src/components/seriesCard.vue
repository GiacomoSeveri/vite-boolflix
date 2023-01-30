<script>
import { store } from './data/store'
export default {
    name: 'seriesCard',
    data() {
        return {
            store,
            imgTunnel: 'https://image.tmdb.org/t/p/w342/'
        }
    },
    methods: {
        voteSerie(i) {
            return Math.ceil(parseInt(this.store.series[i].vote_average) / 2)
        },
    }
}
</script>

<template>
    <h1 v-show="store.series.length >= 1" class="my-5 text-danger text-center" type="button">SERIE TV</h1>
    <div class="container">
        <ul class="row row-cols-4 d-flex justify-content-start">
            <li class="my-3 d-flex justify-content-center m-0" v-for="(serie, i) in store.series" :key="serie.id">
                <figure>
                    <img class="m-0 cover" :src="imgTunnel + serie.poster_path" :alt="serie.name">
                    <div class="caption">
                        <h3 class="text-danger-emphasis">{{ serie.name }}</h3>
                        <h5 class="text-danger">{{ serie.original_name }}</h5>
                        <span class="text-light">{{ serie.overview }}</span>
                        <div class="d-flex justify-content-around mt-3">
                            <img class="flag text-light" :src="`img/${serie.original_language}.png`"
                                :alt="serie.original_language">
                            <i v-for="n in 5" :class="n <= voteSerie(i) ? 'fa-solid' : 'fa-regular'"
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