<template>
    <div id="movieTable">
        <table>
            <thead>
            <tr>
                <th>Title</th>
                <th>Year</th>
                <th>Cast</th>
                <th>Genre</th>
            </tr>
            </thead>
            <tbody v-bind:key="movie" v-for="movie in collection.slice(0,moviesToDisplay)">
            <td>{{movie.title}}</td>
            <td>{{movie.year}}</td>
            <td>

                <p v-bind:key="cast" v-for="cast in movie.cast">
                    {{cast}}
                </p>
            <td>
                <p v-bind:key="genre" v-for="genre in movie.genres">
                    {{genre}}
                </p>
            </td>
            </tbody>
            <tr>
                <td colspan="4"><button v-on:click="moviesToDisplay+=10">Load 10 more</button></td>
            </tr>
        </table>
        <div>

        </div>
    </div>
</template>

<script>
    import movies from '../assets/movies'
    import {eventBus} from "../main";

    let moviesToDisplay = 10;
    let collection = movies;

    export default {
        name: "MyTable",
        props: {
            filterTitle: {
                type: String
            }
        },
        data() {
            return {
                collection,
                moviesToDisplay,
                moviesJson: movies,
                frombrother: ""
            }
        },
        created() {
            eventBus.$on('filterEvent', (message) => {
                this.collection = message;
            });
        }
    }
</script>

<style scoped>
    table {
        margin-left:auto;
        margin-right:auto;
    }

    button {
        width: 100%;
        display: block;
    }
</style>