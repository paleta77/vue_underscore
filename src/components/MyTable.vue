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
            <tbody v-bind:key="movie" v-for="movie in moviesJson.slice(0,moviesToDisplay)">
                <td>{{movie.title}}</td>
                <td>{{movie.year}}</td>
                <td>
                    <ul>
                        <li v-bind:key="cast" v-for="cast in movie.cast">
                            {{cast}}
                        </li>
                    </ul>
                </td>
                <td>
                    <ul>
                        <li v-bind:key="genre" v-for="genre in movie.genres">
                            {{genre}}
                        </li>
                    </ul>
                </td>
            </tbody>
        </table>
        <button v-on:click="moviesToDisplay+=10">Load 10 more</button>
    </div>
</template>

<script>
    import movies from '../assets/movies'
    let moviesToDisplay = 10;

    export default {
        name: "MyTable",
        data() {
            return {
                moviesToDisplay,
                moviesJson: movies,
            }
        }
    }
</script>

<style scoped>

</style>