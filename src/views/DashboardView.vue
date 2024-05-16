<template>
    <div class="bg-blue-400">
      <div class="navbar-container">
        <section>
          <img src="/src/assets/img/car.png" alt="" />
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
            <i class="fa-solid fa-pen-to-square"></i>
            <button @click="editarPerfil">Meu perfil</button>
            <br>
            <i class="fa-solid fa-chevron-right chevron"></i>
            <button @click="sair">Sair</button>
          </div>
        </section>
      </div>
    </div>
    <router-view />
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
  
  const modulos = [
    {
      name: "Home",
      href: "/home",
    },
    {
      name: "Gestão de veículos",
      href: "/gestao-veiculos",
    },
  ];
  </script>