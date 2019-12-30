<template>
    <div>
        <div v-bind:key="genre" v-for="genre in genres">
            <b>{{genre}}</b>
            <p v-bind:key="movie" v-for="movie in filterByGenre(genre).splice(0,3)">{{movie.title}}</p>
        </div>
    </div>
</template>

<script>
    import genres from '../assets/genres'
    import movies from '../assets/movies'
    import {_} from 'vue-underscore';

    export default {
        name: "ByGenresList",
        data () {
            return{
                genres,
            }
        },
        methods: {
            filterByGenre(genre){
                let genreFilter = genre;
                let genreCollection = _.filter(movies, function (element) {
                    return element.genres.toString().toLowerCase().indexOf(genreFilter.toLowerCase().toLowerCase()) != -1;
                });
                return genreCollection;
            }
        }
    }
</script>

<style scoped>

</style>