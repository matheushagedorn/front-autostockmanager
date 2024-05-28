<<<<<<< HEAD
<template>
  <div class="px-4 py-5 my-5 text-center w-100">
    <img class="d-block mx-auto mb-4" src="../assets/img/car.png" alt="" width="96" height="96">
    <h1 class="display-5 fw-bold">Autostock Manager</h1>
    <div class="col-lg-6 mx-auto">
      <p class="lead mb-4">Escolha um dos módulos à esquerda para começar a usar o sistema</p>
    </div>
  </div>

  <div class="b-example-divider"></div>
</template>
  
<script setup>
  import TituloPagina from '../components/TituloPagina.vue';
</script>

<style scoped>
.b-example-divider {
  height: 3rem;
  background-color: rgba(0, 0, 0, .1);
  border: solid rgba(0, 0, 0, .15);
  border-width: 1px 0;
  box-shadow: inset 0 .5em 1.5em rgba(0, 0, 0, .1), inset 0 .125em .5em rgba(0, 0, 0, .15);
}

@media (min-width: 992px) {
  .rounded-lg-3 { border-radius: .3rem; }
}

</style>
=======
<template>
    <div class="home">
      <div class="home-container">
        <TituloPagina titulo="Home" class="home-container-title"/>
        <h2>Seja bem vindo ao AutoStock Manager!</h2>
        <p>Escolha um dos módulos à esquerda para utilizar o sistema</p>
      </div>
    </div>
</template>
  
<script setup>
  import TituloPagina from '../components/TituloPagina.vue';
</script>
>>>>>>> 1dffc7bce3d9a897a33aec2b9613e9a2dae63bb6
