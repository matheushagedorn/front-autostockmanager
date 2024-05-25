<script setup>
import { onBeforeMount } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

onBeforeMount(() => {
  router.push({ name: 'login' })
})

</script>

<template>
  <div class="vh-100">
    <router-view/>
  </div>
</template>