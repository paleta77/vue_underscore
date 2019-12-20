<template>
    <div>
        <table id="movieTable">
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
        </table>
        <button v-on:click="moviesToDisplay+=10">Load 10 more</button>
        <button v-on:click="filterCollection('shrek')">filter</button>
    </div>
</template>

<script>
    import {_} from 'vue-underscore';
    import movies from '../assets/movies'

    let moviesToDisplay = 10;
    let yearFilter = '1999';
    let collection = _.filter(movies, function (element) {
        return element.year.toString().toLowerCase().indexOf(yearFilter.toString().toLowerCase()) != -1;
    });

    let titleFilter = 'matrix';
    collection = _.filter(collection, function (element) {
        return element.title.toString().toLowerCase().indexOf(titleFilter.toString().toLowerCase()) != -1;
    });

    export default {
        name: "MyTable",
        props: {
            filterTitle: {
                type: String
            }
        },
        methods: {
            filterCollection: function (title) {
                this.collection = _.filter(movies, function (element) {
                    return element.title.toLowerCase().indexOf(title.toLowerCase()) != -1;
                });
            },

        },
        data() {
            return {
                collection,
                moviesToDisplay,
                moviesJson: movies,
            }
        }
    }
</script>

<style scoped>

</style>