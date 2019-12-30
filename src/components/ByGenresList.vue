<template>
    <div>
        28795
        <div v-bind:key="actor" v-for="actor in getActors()">
            <b>{{actor}}</b>
            <p v-bind:key="movieOfActor" v-for="movieOfActor in getActorMovies(actor)">{{movieOfActor.title}}</p>
        </div>
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

    let collection = movies;

    export default {
        name: "ByGenresList",
        data () {
            return{
                genres,
                collection
            }
        },
        methods: {
            filterByGenre(genre){
                let genreFilter = genre;
                let genreCollection = _.filter(movies, function (element) {
                    return element.genres.toString().toLowerCase().indexOf(genreFilter.toLowerCase().toLowerCase()) != -1;
                });
                return genreCollection;
            },
            getActors(){
                let actors = [];
                for(let i = 0; i<movies.length; i++){
                    actors.push(movies[i].cast);
                }
                let joinedActors = _.flatten(actors);
                let uniqActors = _.unique(joinedActors.splice(joinedActors.length-10, joinedActors.length-1));
                return uniqActors;
            },
            getActorMovies(actorName){
                let actorMovies = _.filter(collection, function (element) {
                    return element.cast.toString().toLowerCase().indexOf(actorName.toLowerCase().toLowerCase()) != -1;
                });
                return actorMovies;
            }
        }
    }
</script>

<style scoped>

</style>