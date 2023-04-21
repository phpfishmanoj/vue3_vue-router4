<script setup>
import { ref, onMounted } from "vue";
import { useRoute, useRouter } from "vue-router";

const props = defineProps({
    id: {
        type: String,
        required: true
    }
})

const queryMovie = ref({});
const isLoading = ref(true);
const route = useRoute();
const router = useRouter();

onMounted(async () => {
    //const result = await fetch(`http://localhost:3000/movies/${route.params.id}`);
    const result = await fetch(`http://localhost:3000/movies/${parseInt(props.id)}`);
    if (result.status === 404) {
        router.push({ name: 'NotFound' });
    }
    const response = await result.json();
    console.log(response)
    queryMovie.value = response;
    isLoading.value = false;
})

</script>
<template>
    <div class="span">MovieDetails: {{ $route.params.id }}</div>

    <div class="grid grid-cols-3 gap-4">
        <div class="card" style="width: 18rem;">
            <img class="card-img-top" :src="queryMovie.poster" :alt="queryMovie.title">
            <div class="card-body">
                <h5 class="card-title">{{ queryMovie.title }}</h5>
                <p class="card-text">{{ queryMovie.year }}</p>
                <p class="card-text">{{ queryMovie.runtime }}</p>
            </div>
            <button @click="$route.back()">Go Back</button>
        </div>
    </div>
</template>