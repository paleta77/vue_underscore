<template>
    <div>
        <input type="text" v-model="form.title"/>
        <button type="button" @click="messageFiltering">filter123</button>
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
                  title: ''
              }
          }
        },
        methods: {
            messageFiltering() {
                let yearFilter = '';
                let collection = _.filter(movies, function (element) {
                    return element.year.toString().toLowerCase().indexOf(yearFilter.toString().toLowerCase()) != -1;
                });

                let titleFilter = this.form.title;
                collection = _.filter(collection, function (element) {
                    return element.title.toString().toLowerCase().indexOf(titleFilter.toString().toLowerCase()) != -1;
                });

                let castFilter = '';
                collection = _.filter(collection, function (element) {
                    return element.cast.toString().toLowerCase().indexOf(castFilter.toLowerCase().toLowerCase()) != -1;
                });

                let genreFilter = 'horror';
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