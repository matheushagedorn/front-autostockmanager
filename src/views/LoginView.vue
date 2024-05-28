<template>
    <div class="container-fluid bg-primary" style="user-select: none;">
        <div class="container d-flex flex-column align-items-center justify-content-center vh-100 bg-white">
            <img src="/src/assets/img/car.png" style="width: 20rem; height: 20rem;" alt="Carro">
            <h1>AutoStock Manager</h1>
            
            <div class="d-flex flex-column align-items-start justify-content-start gap-2 mb-4" style="margin: 1rem">
                <div class="form-floating">
                    <input type="email" class="form-control" id="matricula" placeholder="Matrícula do usuário" maxlength="6">
                    <label for="matricula">Matrícula do usuário</label>
                  </div>
                  <div class="form-floating">
                    <input type="password" class="form-control" id="senha" placeholder="Senha" minlength="5">
                    <label for="senha">Senha</label>
                  </div>
            </div>
            <router-link to="home"><button class="btn btn-primary">Entrar</button></router-link>
            <router-link to="register"><button style="margin-top: 0.75rem;" class="btn btn-primary">Registre-se</button></router-link>
        </div>
    </div>
</template>