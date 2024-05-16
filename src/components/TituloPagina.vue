<template>
    <div class="row">
        <h1>{{ titulo }}</h1>
        <router-link v-if="link" :to="link">
            <i class="fa-solid fa-circle-arrow-left"></i>
        </router-link>
    </div>
</template>

<script setup>
defineProps({
    titulo: String,
    link: String
})
</script>