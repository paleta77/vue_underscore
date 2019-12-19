<template>
    <form id="filterForm">
        <input type="text" v-model="titleFilter">
        {{titleFilter}}
    </form>
</template>

<script>
    export default {
        name: "FilterForm"
    }
</script>

<style scoped>

</style>