<template>
    <div id="content">
        <GridView></GridView>
        <ListView></ListView>
    </div>
</template>

<script>

import GridView from './Grid.vue'
import ListView from './List.vue'

export default {
    name: "Content",
    components: {
        GridView,
        ListView,
    }
}
</script>

<style lang="scss" scoped>
    #content {
        height: 100%;
        width: 100%;
        display: flex;
        justify-content: space-around;
        align-items: center;
        flex-direction: column;
        margin-top: 25px;
    }
</style>