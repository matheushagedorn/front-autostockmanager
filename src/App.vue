<script setup>
import { onBeforeMount } from 'vue'
import { useRouter } from 'vue-router' // Removi RouterView daqui, pois não é necessário

const router = useRouter()

onBeforeMount(() => {
  router.push({ name: 'login' }) // Aqui ocorre o erro
})
</script>

<template>
  <div>
    <router-view/>
  </div>
</template>
