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
            <tbody v-bind:key="movie" v-for="movie in moviesJson.slice(2220,2230)">
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
    </div>
</template>

<script>
    import movies from '../assets/movies'

    export default {
        name: "MyTable",
        data() {
            return {
                moviesJson: movies,
            }
        }
    }
</script>

<style scoped>

</style>