<script setup>

defineProps({
    movie: Object
});

</script>
<template>
    <div class="card" style="width: 18rem;">
        <!-- <RouterLink :to="`movies/${movie.id}`"> -->
        <RouterLink :to="{ name: 'MovieDetails', params: { id: movie.id } }">
            <img class="card-img-top" :src="movie.poster" :alt="movie.title">
            <div class="card-body">
                <h5 class="card-title">{{ movie.title }}</h5>
                <p class="card-text">{{ movie.year }}</p>
                <p class="card-text">{{ movie.runtime }}</p>
            </div>
        </RouterLink>
    </div>
</template>