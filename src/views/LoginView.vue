<template>
    <div class="container-fluid">
        <div class="container d-flex flex-column align-items-center justify-content-center">
            <img src="/src/assets/img/car.png" style="width: 20rem; height: 20rem;" alt="Carro">
            <h1>AutoStock Manager</h1>
            
            <div class="d-flex flex-column align-items-start justify-content-start gap-2 mb-4">
                <label for="matricula">Matrícula do Usuário:</label>
                <input type="email" id="matricula" placeholder="Matrícula do Usuário">
                <label for="senha">Senha:</label>
                <input type="password" id="senha" placeholder="••••••••">
            </div>
            <router-link to="home"><button>Entrar</button></router-link>
            <router-link to="register"><button style="margin-top: 0.75rem;">Registre-se</button></router-link>
        </div>
    </div>
</template>