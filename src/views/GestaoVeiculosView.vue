<template>
  <div class="d-flex justify-content-center align-items-center w-100 vh-100">
    <div class="col-10">
      <TituloPagina
        titulo="Gestão de veículos"
        link="/home"
      >    
      <template v-slot:button>
        <button class="btn btn-secondary" data-bs-toggle="modal" data-bs-target="#modal_cadastro">
          <i class="fa-solid fa-plus pe-2"></i>Adicionar veículo
        </button>
      </template>
      </TituloPagina>
      <hr>
      <div class="container-fluid" style="height: 40rem; overflow-y: scroll">
        <table class="table table-light table-striped table-hover">
          <thead>
            <tr>
              <th class="text-center">#</th>
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
            <tr v-for="(carro, index) in data" :key="carro.id">
              <td class="text-center">{{ index + 1 }}</td>
              <td>{{ carro.modelo }}</td>
              <td>{{ carro.marca }}</td>
              <td>{{ carro.ano }}</td>
              <td>{{ carro.cor }}</td>
              <td>{{ carro.quilometragem }}</td>
              <td>{{ carro.valor }}</td>
              <td><i :class="['fa-solid', carro.ativo ? 'fa-check' : 'fa-xmark']"></i></td>
              <td>
                <div class="dropdown">
                  <button class="btn btn-outline-primary" type="button" data-bs-toggle="dropdown" aria-expanded="false">
                    ...
                  </button>
                  <ul class="dropdown-menu">
                    <li>
                      <button class="dropdown-item" @click="activateCar(carro.id)">
                        <i :class="['fa-solid', carro.ativo ? 'fa-xmark' : 'fa-check']"></i> Ativar/Inativar
                      </button>
                    </li>
                    <li>
                      <button class="dropdown-item" data-bs-toggle="modal" data-bs-target="#modal_edicao" @click="fetchingCar(carro.id)">
                        <i class="fa-solid fa-pen"></i> Editar
                      </button>
                    </li>
                    <li>
                      <button class="dropdown-item" @click="deleteCar(carro.id)">
                        <i class="fa-solid fa-trash"></i> Excluir
                      </button>
                    </li>
                  </ul>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>

  <div class="modal fade" id="modal_cadastro" tabindex="-1" aria-labelledby="modal_cadastro" aria-hidden="true">
    <div class="modal-dialog modal-lg modal-dialog-centered">
      <div class="modal-content">
        <div class="modal-header">
          <h1 class="modal-title fs-5" id="modal_cadastro"><i class="fa-solid fa-pen pe-2"></i>Criar novo carro</h1>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <div class="d-flex flex-column gap-2">
            <div class="form-floating">
              <input type="text" class="form-control" id="modelo_criacao" placeholder="Modelo do carro">
              <label for="modelo">Modelo do carro</label>
            </div>
            <div class="form-floating">
              <input type="text" class="form-control" id="marca_criacao" placeholder="Marca do carro">
              <label for="marca">Marca do carro</label>
            </div>
            <div class="form-floating">
              <input type="number" class="form-control" id="ano_criacao" placeholder="Ano do carro">
              <label for="ano">Ano do carro</label>
            </div>
            <div class="form-floating">
              <input type="text" class="form-control" id="cor_criacao" placeholder="Cor do carro">
              <label for="cor">Cor do carro</label>
            </div>
            <div class="form-floating">
              <input type="number" class="form-control" id="quilometragem_criacao" placeholder="Quilometragem do carro">
              <label for="quilometragem">Quilometragem do carro</label>
            </div>
            <div class="form-floating">
              <input type="number" class="form-control" id="valor_criacao" placeholder="Valor do carro">
              <label for="valor">Valor do carro</label>
            </div>
            <div class="form-check form-switch">
              <input class="form-check-input" type="checkbox" id="ativo_criacao">
              <label class="form-check-label" for="ativo">Ativo</label>
            </div>
          </div>
        </div>
        <div class="modal-footer d-flex justify-content-end">
          <button type="button" class="btn btn-outline-success" @click="createCar()">Salvar alterações<i class="fa-solid fa-pen ps-2"></i></button>
        </div>
      </div>
    </div>
  </div>

  <div class="modal fade" id="modal_edicao" tabindex="-1" aria-labelledby="modal_edicao" aria-hidden="true">
    <div class="modal-dialog modal-lg modal-dialog-centered">
      <div class="modal-content">
        <div class="modal-header">
          <h1 class="modal-title fs-5" id="modal_edicao"><i class="fa-solid fa-pen pe-2"></i>Editar Carro</h1>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <div class="d-flex flex-column gap-2">
            <div class="form-floating">
              <input type="text" class="form-control" id="modelo" placeholder="Modelo do carro">
              <label for="modelo">Modelo do carro</label>
            </div>
            <div class="form-floating">
              <input type="text" class="form-control" id="marca" placeholder="Marca do carro">
              <label for="marca">Marca do carro</label>
            </div>
            <div class="form-floating">
              <input type="number" class="form-control" id="ano" placeholder="Ano do carro">
              <label for="ano">Ano do carro</label>
            </div>
            <div class="form-floating">
              <input type="text" class="form-control" id="cor" placeholder="Cor do carro">
              <label for="cor">Cor do carro</label>
            </div>
            <div class="form-floating">
              <input type="number" class="form-control" id="quilometragem" placeholder="Quilometragem do carro">
              <label for="quilometragem">Quilometragem do carro</label>
            </div>
            <div class="form-floating">
              <input type="number" class="form-control" id="valor" placeholder="Valor do carro">
              <label for="valor">Valor do carro</label>
            </div>
            <div class="form-check form-switch">
              <input class="form-check-input" type="checkbox" id="ativo">
              <label class="form-check-label" for="ativo">Ativo</label>
            </div>
          </div>
        </div>
        <div class="modal-footer d-flex justify-content-between">
          <button type="button" class="btn btn-outline-danger" @click="deleteCar(idcarro)"><i class="fa-solid fa-trash pe-2"></i>Excluir</button>
          <button type="button" class="btn btn-outline-success" @click="updateCar(idcarro)">Salvar alterações<i class="fa-solid fa-pen ps-2"></i></button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import TituloPagina from "../components/TituloPagina.vue";
import { onMounted, ref } from "vue";
import Swal from 'sweetalert2';

const data = ref([]);
const carro = ref({});
const idcarro = ref(0);

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
  } catch (error) {
    console.error('Error fetching carros:', error);
  }
}

async function createCar() {
  const modelo = document.getElementById('modelo_criacao').value;
  const marca = document.getElementById('marca_criacao').value;
  const ano = document.getElementById('ano_criacao').value;
  const cor = document.getElementById('cor_criacao').value;
  const quilometragem = document.getElementById('quilometragem_criacao').value;
  const ativo = document.getElementById('ativo_criacao').checked;
  const valor = document.getElementById('valor_criacao').value;

  const body = JSON.stringify({
    modelo,
    marca,
    ano,
    cor,
    quilometragem,
    ativo,
    valor,
  });

  await fetch(`http://localhost:8080/carros`, {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
    },
    body,
  });

  Swal.fire({
    title: "Carro criado!",
    text: "Carro criado com sucesso.",
    icon: "success"
  }).then(() => {
    const modal = document.getElementById('modal_cadastro');
    const modalInstance = bootstrap.Modal.getInstance(modal);
    modalInstance.hide();
    listar();
  });
}

function fetchingCar(id) {
  carro.value = data.value.find((user) => user.id === id);

  idcarro.value = carro.value.id;
  document.getElementById('modelo').value = carro.value.modelo;
  document.getElementById('marca').value = carro.value.marca;
  document.getElementById('ano').value = carro.value.ano;
  document.getElementById('cor').value = carro.value.cor;
  document.getElementById('quilometragem').value = carro.value.quilometragem;
  document.getElementById('ativo').checked = carro.value.ativo;
  document.getElementById('valor').value = carro.value.valor;
}

async function updateCar(id) {
  const modelo = document.getElementById('modelo').value;
  const marca = document.getElementById('marca').value;
  const ano = document.getElementById('ano').value;
  const cor = document.getElementById('cor').value;
  const quilometragem = document.getElementById('quilometragem').value;
  const ativo = document.getElementById('ativo').checked;
  const valor = document.getElementById('valor').value;

  const body = JSON.stringify({
    modelo,
    marca,
    ano,
    cor,
    quilometragem,
    ativo,
    valor,
  });

  await fetch(`http://localhost:8080/carros/${id}`, {
    method: 'PUT',
    headers: {
      'Content-Type': 'application/json',
    },
    body,
  });

  Swal.fire({
    title: "Carro alterado!",
    text: "Carro alterado com sucesso.",
    icon: "success"
  }).then(() => {
    listar();
  });
}

async function activateCar(id) {
  carro.value = data.value.find((user) => user.id === id);
  const ativo = !carro.value.ativo;

  const body = JSON.stringify({
    ativo,
  });

  await fetch(`http://localhost:8080/carros/status/${id}`, {
    method: 'PUT',
    headers: {
      'Content-Type': 'application/json',
    },
    body,
  });

  Swal.fire({
    title: "Carro alterado!",
    text: "Carro ativado/inativado com sucesso.",
    icon: "success"
  }).then(() => {
    listar();
  });
}

function deleteCar(id) {
  fetch(`http://localhost:8080/carros/${id}`, {
    method: 'DELETE',
    headers: {
      'Content-Type': 'application/json',
    },
});

  Swal.fire({
    title: "Carro deletado!",
    text: "Carro deletado com sucesso.",
    icon: "success"
  }).then(() => {
    listar();
  });
}
</script>
