<<<<<<< Updated upstream
<template>
    <div class="d-flex justify-content-center align-items-center vh-100">
      <div class="">
        <TituloPagina
          titulo="Gestão de veículos"
          class="gestao-veiculos-container-title"
          link="/home"
        />
        <div class="gestao-veiculos-container-crud">
          <table>
            <tr>
              <th>Modelo</th>
              <th>Marca</th>
              <th>Ano</th>
              <th>Cor</th>
              <th>Quilometragem</th>
              <th>Valor da revenda</th>
              <th>Status</th>
            </tr>
            <tr
            v-for="carro in data"
            :key="carro.id">
              <td>{{ carro.modelo }}</td>
              <td>{{ carro.marca }}</td>
              <td>{{ carro.ano }}</td>
              <td>{{ carro.cor }}</td>
              <td>{{ carro.quilometragem }}</td>
              <td>{{ carro.valor }}</td>
              <td>{{ carro.status }}</td>
            </tr>
          </table>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import TituloPagina from "../components/TituloPagina.vue";
  import { onMounted, ref } from "vue";
  
  const data = ref([]);
  
  onMounted(async () => {
    await listar();
  });
  
  async function listar() {
    try {
      const response = await fetch('http://localhost:8080/carros', {
        method: 'GET',
        headers: {
          'Content-Type': 'application/json',
        }
      });
  
      let responseData = await response.json();
      data.value = responseData
      
      console.log(data);
    } catch (error) {
      console.error('Error fetching carros:', error);
    }
  }
  
=======
<template>
    <div class="gestao-veiculos">
      <div class="gestao-veiculos-container">
        <TituloPagina
          titulo="Gestão de veículos"
          class="gestao-veiculos-container-title"
          link="/home"
        />
        <div class="gestao-veiculos-container-crud">
          <table>
            <tr>
              <th>Modelo</th>
              <th>Marca</th>
              <th>Ano</th>
              <th>Cor</th>
              <th>Quilometragem</th>
              <th>Valor da revenda</th>
              <th>Status</th>
            </tr>
            <tr
            v-for="carro in data"
            :key="carro.id">
              <td>{{ carro.modelo }}</td>
              <td>{{ carro.marca }}</td>
              <td>{{ carro.ano }}</td>
              <td>{{ carro.cor }}</td>
              <td>{{ carro.quilometragem }}</td>
              <td>{{ carro.valor }}</td>
              <td>{{ carro.status }}</td>
            </tr>
          </table>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import TituloPagina from "../components/TituloPagina.vue";
  import { onMounted, ref } from "vue";
  
  const data = ref([]);
  
  onMounted(async () => {
    await listar();
  });
  
  async function listar() {
    try {
      const response = await fetch('http://localhost:8080/carros', {
        method: 'GET',
        headers: {
          'Content-Type': 'application/json',
        }
      });
  
      let responseData = await response.json();
      data.value = responseData
      
      console.log(data);
    } catch (error) {
      console.error('Error fetching carros:', error);
    }
  }
  
>>>>>>> Stashed changes
  </script>