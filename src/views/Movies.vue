<script setup>
import { ref, onMounted } from 'vue';
import MovieCard from '../components/MovieCards.vue';
const movieList = ref([]);
const isLoading = ref(true);

onMounted(async () => {
    const result = await fetch('http://localhost:3000/movies/')
    const response = await result.json();
    movieList.value = response;
    isLoading.value = false;
    // .then((response) => response.json())
    // .then(apiMovies => {
    //     movieList.value = apiMovies;

    // }).catch(function () {
    //     console.log("error");
    // });

});
</script>

<template>
    <div>
        <h1>Movies</h1>
    </div>
    <div v-if="isLoading" class="max-w-sm mx-auto"><span class="text-2xl font-bold text-indigo-700">Is Loading...</span>
    </div>
    <div class="grid grid-cols-3 gap-4" v-else>
        <MovieCard v-for="movie in movieList" :key="movie.id" :movie="movie" />
    </div>
</template>