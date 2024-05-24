<template>
    <div class="container-fluid bg-primary" style="user-select: none;">
        <div class="container d-flex flex-column align-items-center justify-content-center vh-100 bg-white">
            <img src="/src/assets/img/car.png" alt="Carro" style="width: 20rem; height: 20rem;">
            <h1>AutoStock Manager</h1>

            <div class="d-flex flex-column align-items-center justify-content-center gap-2 mb-4" style="margin: 1rem">
                <div class="form-floating">
                    <input type="email" class="form-control" id="matricula" placeholder="Matrícula do usuário">
                    <label for="matricula">Matrícula do usuário</label>
                </div>
                <div class="form-floating">
                    <input type="password" class="form-control" id="senha" placeholder="Senha" minlenght="5">
                    <label for="senha">Senha</label>
                </div>
                <div class="form-floating">
                    <input type="password" class="form-control" id="confirmaSenha" placeholder="Confirme sua senha" minlenght="5">
                    <label for="confirmaSenha">Confirme sua senha</label>
                </div>
                <div class="form-floating">
                    <input type="nome" class="form-control" id="nome" placeholder="Nome completo">
                    <label for="nome">Nome completo</label>
                </div>
                <div class="form-floating">
                    <input type="email" class="form-control" id="email" placeholder="Email">
                    <label for="email">Email</label>
                </div>
                <button class="btn btn-primary mb-4" style="margin-top: 0.75rem" @click="cadastrar">Cadastre-se</button>
                <router-link to="/"><button class="btn btn-primary">Voltar para Login</button></router-link>
            </div>
        </div>
    </div>
</template>

<script setup>
import { useRouter } from 'vue-router'

const router = useRouter()

async function cadastrar() {
    const matricula = document.getElementById('matricula').value;
    const senha = document.getElementById('senha').value;
    const confirmaSenha = document.getElementById('confirmaSenha').value;
    const nomeCompleto = document.getElementById('nome').value;
    const email = document.getElementById('email').value;

    if (senha !== confirmaSenha) {
        alert('As senhas não coincidem!');
        return;
    }

    const response = await fetch('http://localhost:8080/usuarios', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
        },
        body: JSON.stringify({
            matricula: matricula,
            senha: senha,
            nome: nomeCompleto,
            email: email,
        }),
    });

    if (response.ok) {
        alert('Usuário cadastrado com sucesso!');
        await router.push({ name: 'login' });
    } else {
        alert('Erro ao cadastrar usuário!');
    }
}
</script>