<template>
    <form id="filterForm">
        <button type="button" @click="messagefiltering">filter123</button>
    </form>
</template>

<script>
    import {eventBus} from "../main";

    export default {
        name: "FilterForm",
        methods: {
            messagefiltering() {
                eventBus.$emit('filterEvent', 'test123')
            }
        }
    }
</script>

<style scoped>

</style>