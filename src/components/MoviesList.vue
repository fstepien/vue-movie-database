<template>
<ul>
    <li v-for="movie in movies" :key="movie.id">
    <Movie :movie="movie" />
    </li>
</ul>
</template>

<script>
import Movie from './Movie.vue'
export default {
    name: 'MoviesList',
    data() {
        return {
            movies: []
        }
    },
    created: function() {
    this.fetchData()
    },
    methods: {
        fetchData: async function() {
            try {
                const res = await fetch('https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=ab8356e075fc49f45bcecd2802a2c5dd')
                const movies = await res.json()
                this.movies = movies.results
            } catch (e) {
                console.log(e)
            }
        }
},
    components: {
    Movie
}

}
</script>

<style scoped>
    ul {
        display: grid;
        list-style: none;
        padding: 1rem;
        margin: 0;
        grid-row-gap: 1rem;
        grid-template-columns: repeat(auto-fit, minmax(179px, 1fr));
    }
</style>
