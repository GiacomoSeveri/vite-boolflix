<script>
import { store } from './data/store'
import filmCard from './filmCard.vue';
import seriesCard from './seriesCard.vue';

export default {
    name: 'card',
    components: { filmCard, seriesCard }
}
</script>

<template>
    <filmCard></filmCard>
    <seriesCard></seriesCard>
</template>

<style lang="scss" scoped>

</style>