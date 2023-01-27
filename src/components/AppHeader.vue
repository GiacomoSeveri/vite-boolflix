<script>
import { store } from './data/store'
export default {
    name: 'AppHeader',
    data() {
        return {

            store
        }
    },
    emits: ['research']

}
</script>

<template>
    <div class="d-flex align-items-center custom-bgc">
        <h1 class="m-2 fw-bold text-danger" type="button">BOOLFLIX</h1>
        <input v-model="store.searchTitle" type="text" class="form-control " placeholder="cosa vuoi vedere?">
        <button @click="$emit('research', store.searchTitle)" class="btn btn-outline-danger m-3">CERCA</button>
    </div>
</template>

<style lang="scss" scoped>
.custom-bgc {
    background-color: #000000;
}
</style>