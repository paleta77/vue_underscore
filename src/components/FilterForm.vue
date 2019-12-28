<template>
    <div>
        <input type="text" v-model="form.title" placeholder="Title"/>
        <input type="text" v-model="form.year" placeholder="Year"/>
        <input type="text" v-model="form.cast" placeholder="Cast"/>
        <input type="text" v-model="form.genre" placeholder="Genre"/>
        <button type="button" @click="messageFiltering">Filter</button>
    </div>

</template>

<script>
    import {eventBus} from "../main";
    import {_} from "vue-underscore";
    import movies from "../assets/movies";

    export default {
        name: "FilterForm",
        data() {
          return {
              form:{
                  title: '',
                  year: '',
                  cast: '',
                  genre: '',
              }
          }
        },
        methods: {
            messageFiltering() {
                let yearFilter = this.form.year;
                let collection = _.filter(movies, function (element) {
                    return element.year.toString().toLowerCase().indexOf(yearFilter.toString().toLowerCase()) != -1;
                });

                let titleFilter = this.form.title;
                collection = _.filter(collection, function (element) {
                    return element.title.toString().toLowerCase().indexOf(titleFilter.toString().toLowerCase()) != -1;
                });

                let castFilter = this.form.cast;
                collection = _.filter(collection, function (element) {
                    return element.cast.toString().toLowerCase().indexOf(castFilter.toLowerCase().toLowerCase()) != -1;
                });

                let genreFilter = this.form.genre;
                collection = _.filter(collection, function (element) {
                    return element.genres.toString().toLowerCase().indexOf(genreFilter.toLowerCase().toLowerCase()) != -1;
                });
                eventBus.$emit('filterEvent', collection)
            }
        }
    }
</script>

<style scoped>

</style>