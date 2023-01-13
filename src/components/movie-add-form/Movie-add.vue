<template>
    <div class="movie-add py-2">
        <h3>Movie add </h3>
        <form class="d-flex add-form gap-1" @submit.prevent>
            <input type="text" class="form-control new-movie-input" placeholder="Movie" :value="name"
                @input="name = $event.target.value">
            <input type="number" class="form-control new-movie-input" placeholder="Movie" :value="views"
                @input="views = $event.target.value">
            <button class="btn btn-outline-dark" type="submit" @click="addMovie">Qo'shish </button>
        </form>
    </div>
</template>

<script>
export default {
    data() {
        return {
            name: "",
            views: "",
        }
    },
    methods: {
        addMovie() {
            if (!this.name || !this.views) return
            const newMovie = {
                name: this.name,
                views: this.views,
                like: false,
                favourite: false,
                id: Date.now(),
            }
            this.$emit("createMovie", newMovie)
            this.name = ""
            this.views = ""
        }
    }
}
</script>
<style scope>
.add-form {
    margin-top: 2rem;
    padding: 1.5rem;
    background-color: #fcfaf5;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>