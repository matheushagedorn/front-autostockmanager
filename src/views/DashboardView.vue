<template>
  <div>
    <div class="navbar-container">
      <section>
        <img src="/src/assets/img/car.png" alt="Car logo" />
        <p>AutoStock</p>
      </section>
      <router-link v-for="item in modulos" :key="item.name" :to="item.href">
        <button>{{ item.name }}</button>
      </router-link>
    </div>
    <div class="navbar-container-perfil">
      <section>
        <div class="navbar-container-perfil-user">
          <div class="navbar-container-perfil-user-btn">
            <button @click="menuUsuario">
              <i class="fa-solid fa-user"></i>
              &nbsp; {{ usuario }}
            </button>
          </div>
        </div>
        <!-- DROPDOWN -->
        <div class="navbar-container-perfil-user-btn-menu" v-if="abreMenu">
          <div class="dropdown-item">
            <i class="fa-solid fa-pen-to-square"></i>
            <button @click="editarPerfil">Meu perfil</button>
          </div>
          <div class="dropdown-item">
            <i class="fa-solid fa-chevron-right chevron"></i>
            <button @click="sair">Sair</button>
          </div>
        </div>
      </section>
    </div>
    <router-view />
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();
const usuario = ref("Matheus Hagedorn");
const abreMenu = ref(false);

async function sair() {
  await router.push({ name: "login" });
}

function menuUsuario() {
  abreMenu.value = !abreMenu.value;
}

function editarPerfil() {
  console.log("Editar perfil clicado");
}

const modulos = [
  {
    name: "Home",
    href: "/home",
  },
  {
    name: "Gestão de veículos",
    href: "/gestao-veiculos",
  },
  {
    name: "Gestão de usuários",
    href: "/gestao-usuarios",
  },
];
</script>

<style scoped>
.navbar-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px;
  background-color: #f8f9fa;
}

.navbar-container section {
  display: flex;
  align-items: center;
}

.navbar-container img {
  height: 40px;
  margin-right: 10px;
}

.navbar-container-perfil {
  display: flex;
  align-items: center;
  position: relative;
}

.navbar-container-perfil-user {
  display: flex;
  align-items: center;
}

.navbar-container-perfil-user-btn {
  position: relative;
}

.navbar-container-perfil-user-btn-menu {
  position: absolute;
  top: 100%;
  right: 0;
  background-color: white;
  border: 1px solid #ccc;
  padding: 10px;
  z-index: 10;
}

.dropdown-item {
  display: flex;
  align-items: center;
  padding: 5px 0;
}

.dropdown-item i {
  margin-right: 5px;
}

.dropdown-item button {
  background: none;
  border: none;
  cursor: pointer;
  font: inherit;
  color: inherit;
  padding: 0;
}

.dropdown-item button:hover {
  text-decoration: underline;
}

.chevron {
  margin-left: auto;
}
</style>
