<<<<<<< HEAD
<template>
    <div class="d-flex align-items-center mb-3">
      <router-link v-if="link" :to="link" class="btn btn-link btn-lg active p-0 me-2">
        <i class="fa-solid fa-circle-arrow-left"></i>
      </router-link>
      <h1 class="mb-0">{{ titulo }}</h1>
    </div>
  </template>
  
  <script setup>
  defineProps({
    titulo: String,
    link: String
  });
  </script>
  
=======
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
>>>>>>> 1dffc7bce3d9a897a33aec2b9613e9a2dae63bb6
