<<<<<<< Updated upstream
<template>
  <div class="d-flex justify-content-center align-items-center w-100 vh-100">
    <div class="col-10">
      <TituloPagina
        titulo="Gestão de veículos"
        link="/home"
      />
      <hr>
      <div class="input-group mb-3 col-3">
        <span class="input-group-text" id="basic-addon2">
          <i class="fa-solid fa-magnifying-glass"></i>
        </span>
        <input type="text" class="form-control" placeholder="Procurar..." aria-label="Procurar..." aria-describedby="basic-addon2">
      </div>
      <div class="container-fluid">
        <table class="table table-light table-striped table-hover">
          <thead>
            <tr>
              <th scope="col">#</th>
              <th scope="col">Modelo</th>
              <th scope="col">Marca</th>
              <th scope="col">Ano</th>
              <th scope="col">Cor</th>
              <th scope="col">Quilometragem</th>
              <th scope="col">Valor da revenda</th>
              <th scope="col">Status</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="carro in data" :key="carro.id">
              <th scope="row">{{ carro.id }}</th>
              <td>{{ carro.modelo }}</td>
              <td>{{ carro.marca }}</td>
              <td>{{ carro.ano }}</td>
              <td>{{ carro.cor }}</td>
              <td>{{ carro.quilometragem }}</td>
              <td>{{ carro.valor }}</td>
              <td>{{ carro.status }}</td>
            </tr>
          </tbody>
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
    data.value = responseData;
    console.log(data.value);
  } catch (error) {
    console.error('Error fetching carros:', error);
  }
<<<<<<< HEAD
}
</script>
=======
  
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
>>>>>>> 1dffc7bce3d9a897a33aec2b9613e9a2dae63bb6
