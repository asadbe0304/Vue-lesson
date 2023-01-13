<template>
    <div class="app font-monospace">
        <div class="content">
            <AppInfo :allMoviesCount="movies.length" :favouriteMovie="movies.filter(c => c.favourite).length" />
            <div class=" search-panel">
                <Search :updateHandler="updateHandler" />
                <AppFilter :updateFilterHandler="updateFilterHandler" :filterName="filter"/>
            </div>
            <MovieList :movies="onFilterHandler(onSearchHandler(movies, term), filter)" @onToggle="onToggleHandler"
                @onRemove="onRemoveHandler" />
            <MovieAdd @createMovie="createMovie" />
            <!-- <h1>Hello world</h1> -->
            <!-- <h2>{{ counter }}</h2> -->
            <!-- <button @click="onIncrement" class="btn btn-danger col-1">Add</button> -->
            <!-- <button @click="onDecrement" class="btn btn-warning col-1">Delete</button> -->
        </div>
    </div>

</template>

<script>
import AppInfo from "../src/components/app-info/AppInfo.vue"
import Search from "./components/search-panel/Search.vue"
import MovieAdd from "./components/movie-add-form/Movie-add.vue"
import AppFilter from "./components/app-filter/AppFilter.vue"
import MovieList from "./components/movie-list/MovieList.vue"
export default {
    components: {
        AppInfo,
        Search,
        AppFilter,
        MovieList,
        MovieAdd,
    },
    data() {
        return {
            movies: [
                {
                    name: "Omar",
                    views: 255,
                    like: false,
                    favourite: false,
                    id: 1,
                },
                {
                    name: "Istanbul",
                    views: 834,
                    like: false,
                    favourite: false,
                    id: 2,
                },
                {
                    name: "Turkey",
                    views: 634,
                    like: false,
                    favourite: false,
                    id: 3,
                },
            ],
            term: '',
            filter: '',
        }
    },
    // data() {
    //     return {
    //         counter: 0,
    //     }
    // },
    // methods: {
    //     onIncrement() {
    //         this.counter += 1
    //      },
    //     onDecrement() { 
    //         this.counter -= 1
    //     },
    // }
    methods: {
        createMovie(item) {
            this.movies.push(item)
        },
        onToggleHandler({ id, prop }) {
            this.movies = this.movies.map(item => {
                if (item.id == id) {
                    return { ...item, [prop]: !item[prop] }
                }
                return item
            })
        },
        onRemoveHandler(id) {
            this.movies = this.movies.filter(c => c.id !== id)
        },
        onSearchHandler(arr, term) {
            if (term.length == 0) {
                return arr
            }
            return arr.filter(c => c.name.toLowerCase().indexOf(term) > -1)
        },
        onFilterHandler(arr, filter) {
            switch (filter) {
                case 'popular':
                    return arr.filter(c => c.like)
                case 'Viewers':
                    return arr.filter(c => c.views > 500)
                default:
                    return arr
            }
        },
        updateHandler(term) {
            this.term = term
        },
        updateFilterHandler(filter) {
            this.filter = filter
        }
        // onFavouriteHandler(id) {
        //     const item = this.movies.map(c => {
        //         if (c.id == id) {
        //             c.favourite = !c.favourite
        //         }
        //         return c
        //     })
        // console.log(item);
        // }
    },
}

</script>
<style scoped>
.app {
    height: 100vh;
    color: #000;
}

.content {
    width: 1000px;
    margin: 0 auto;
    padding: 5rem 0;
    min-height: 700px;
    background-color: #fff;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}

.search-panel {
    margin-top: 2rem;
    padding: 1.5rem;
    background-color: #fcfaf5;
    border-radius: 4px;
    box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>