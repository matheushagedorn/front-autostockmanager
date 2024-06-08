<template>
  <div class="d-flex justify-content-center w-100 vh-100">
    <div class="col-10 d-flex flex-column align-items-center mt-5">
      <div class="row mb-2">
        <div class="col-12">
          <div class="border border-4 border-black p-4 rounded-pill bg-dark-subtle">
            <i class="fs-1 fa-solid fa-user"></i> 
          </div>
        </div>
      </div>
      <div class="row mb-4">
        <div class="col-12">
          <h1>
            Matheus Hagedorn
          </h1>
        </div>
      </div>
      <div class="d-flex flex-column bg-dark-subtle border border-dark border-1 rounded-4 p-4 gap-4 w-50">
        <div class="d-flex flex-column">
          <span class="fs-5 fw-semibold">
            CPF
          </span>
          <span class="fs-6">
            123.456.789-00
          </span>
        </div>
        <div class="d-flex flex-column">
          <span class="fs-5 fw-semibold">
            Matrícula
          </span>
          <span class="fs-6">
            123456
          </span>
        </div>
        <div class="d-flex flex-column">
          <span class="fs-5 fw-semibold">
            CPF
          </span>
          <span class="fs-6">
            123.456.789-00
          </span>
        </div>
        <div class="d-flex flex-column">
          <span class="fs-5 fw-semibold">
            Email
          </span>
          <span class="fs-6">
            teste@gmail.com
          </span>
        </div>
      </div>
      <div class="d-flex justify-content-between align-items-center mt-4 gap-4">
        <button class="btn btn-danger fs-5 fw-semibold">
          Excluir
        </button>
        <button class="btn btn-warning fs-5 fw-semibold">
          Editar
        </button>
      </div>
    </div>
  </div>
</template>
  
  <script setup>
  import TituloPagina from "../components/TituloPagina.vue";
  import { onMounted, ref } from "vue";
  
  const data = ref([]);
  const usuario = ref({});
  const idusuario = ref(0);
  
  </script>