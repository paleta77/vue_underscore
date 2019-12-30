<template>
    <div>
        <h2>Movies by actors</h2>
        <div v-bind:key="actor" v-for="actor in getActors()">
            <b>{{actor}}</b>
            <p v-bind:key="movieOfActor" v-for="movieOfActor in getActorMovies(actor)">{{movieOfActor.title}}</p>
        </div>
    </div>
</template>

<script>
    import {_} from "vue-underscore";
    import movies from "../assets/movies";

    export default {
        name: "ByActorList",
        methods: {
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
                let actorMovies = _.filter(movies, function (element) {
                    return element.cast.toString().toLowerCase().indexOf(actorName.toLowerCase().toLowerCase()) != -1;
                });
                return actorMovies;
            }
        }
    }
</script>

<style scoped>

</style>