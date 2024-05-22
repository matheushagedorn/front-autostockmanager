<template>
    <div class="container h-100 d-flex flex-column align-items-center justify-content-center bg-primary gap-4">
        <div class="row">
            <div class="col-12">
                <img src="/src/assets/img/car.png" style="width: 20rem; height: 20rem;" alt="Carro">
                <h1>AutoStock Manager</h1>
            </div>
        </div>
        <div class="row">
            <div class="col-12 d-flex flex-column align-items-center justify-content-center gap-2">
                <label class="fs-5" for="matricula">Matrícula do Usuário:</label>
                <input type="email" id="matricula" placeholder="Matrícula do Usuário">
                <label class="fs-5" for="senha">Senha:</label>
                <input type="password" id="senha" placeholder="••••••••">
            </div>
        </div>
        <div class="row">
            <div class="col-12 d-flex flex-column align-items-center justify-content-center gap-2">
                <router-link to="home"><button>Entrar</button></router-link>
                <router-link to="register"><button style="margin-top: 0.75rem;">Registre-se</button></router-link>
            </div>
        </div>
    </div>
</template>