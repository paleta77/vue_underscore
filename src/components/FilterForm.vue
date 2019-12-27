<template>
    <form id="filterForm">
        <button type="button" @click="messagefiltering">filter123</button>
    </form>
</template>

<script>
    import {eventBus} from "../main";
    import {_} from "vue-underscore";
    import movies from "../assets/movies";

    let yearFilter = '';
    let collection = _.filter(movies, function (element) {
        return element.year.toString().toLowerCase().indexOf(yearFilter.toString().toLowerCase()) != -1;
    });

    let titleFilter = 'star wars';
    collection = _.filter(collection, function (element) {
        return element.title.toString().toLowerCase().indexOf(titleFilter.toString().toLowerCase()) != -1;
    });

    let castFilter = '';
    collection = _.filter(collection, function (element) {
        return element.cast.toString().toLowerCase().indexOf(castFilter.toLowerCase().toLowerCase()) != -1;
    });

    let genreFilter = '';
    collection = _.filter(collection, function (element) {
        return element.genres.toString().toLowerCase().indexOf(genreFilter.toLowerCase().toLowerCase()) != -1;
    });

    export default {
        name: "FilterForm",
        methods: {
            messagefiltering() {
                eventBus.$emit('filterEvent', collection)
            }
        }
    }
</script>

<style scoped>

</style>