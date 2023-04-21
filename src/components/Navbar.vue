<script setup>

</script>
<style>
#navbar {
    margin: 0;
    padding: 0;
    list-style-type: none;
    width: 100px;
}

#navbar li {
    border-left: 10px solid #666;
    border-bottom: 1px solid #666;
}

#navbar a {
    background-color: #949494;
    color: #fff;
    padding: 5px;
    text-decoration: none;
    font-weight: bold;
    border-left: 5px solid #33ADFF;
    display: block;
}
</style>
<template>
    <ul id="navbar">
        <li>
            <RouterLink to="/">Home</RouterLink>
        </li>
        <li><router-link to="/movies">Movies</router-link></li>
        <li>
            <RouterLink to="/about">About us</RouterLink>
        </li>
    </ul>
</template>