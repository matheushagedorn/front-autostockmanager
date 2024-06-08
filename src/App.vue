<script setup>
import { onBeforeMount } from 'vue'
import { useRouter } from 'vue-router'
import { ref } from 'vue'

const router = useRouter()

const userData = ref(null);

onBeforeMount(() => {
  router.push({ name: 'login' })
})

if (localStorage.getItem('user')) {
  userData.value = JSON.parse(localStorage.getItem('user'));
}
</script>

<template>
  <div class="vh-100">
    <router-view/>
  </div>
</template>