<template>
    <ul class="movie__list list-group">
        <MovieItem
        v-for="movie in movies"
        :movie="movie" 
        :key="movies.id" 
        @onToggle="$emit('onToggle', $event)"
        @onRemove="$emit('onRemove', $event)" />
    </ul>
</template>

<script>
import MovieItem from "./../Movie-list-item/movieItem.vue"
export default {
    components: { MovieItem },
    props: {
        movies: {
            type: Array,
            required: true,
        }
    },
}
</script>
<style scope>
.movie__list {
    margin-top: 2rem;
    margin-bottom: 1rem;
    background-color: #fcfaf5;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>