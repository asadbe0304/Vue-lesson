<template>
    <div>
        <label for="movie">Kinolarni Qidirish</label>
        <input type="search" id="movie" class="form-control search-input" @input="changeHandler" :value="term"
            placeholder="kinolarni qidirish">

    </div>
</template>

<script>
export default {
    props: {
        updateHandler: {
            type: Function,
            required: true,
        },
    },
    data() {
        return {
            term: '',
        }
    },

    methods: {
        changeHandler(e) {
            this.term = e.target.value
            this.updateHandler(this.term)
        }
    },
}
</script>

<style scope>
.search-input {
    margin-top: 2rem;
    margin-bottom: 1rem;
    background-color: #fcfaf5;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>