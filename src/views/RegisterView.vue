<template>
    <div class="container-fluid">
        <div class="container d-flex flex-column align-items-center justify-content-center">
            <img src="/src/assets/img/car.png" style="width: 20rem; height: 20rem;" alt="Carro">
            <h1>AutoStock Manager</h1>

            <div class="row">
                <div class="col-12 d-flex flex-column align-items-start justify-content-start gap-2 mb-4">
                    <label for="matricula">Matrícula do Usuário:</label>
                    <input type="text" id="matricula" placeholder="Matrícula" maxlength="5">
                    <label for="senha">Senha:</label>
                    <input type="password" id="senha" placeholder="••••••••" minlegth="8">
                    <label for="confirma-senha">Confirme sua senha:</label>
                    <input type="password" id="confirma-senha" placeholder="••••••••" minlegth="8">
                    <label for="nome-completo">Nome completo:</label>
                    <input type="text" id="nome-completo" placeholder="Nome completo">
                    <label for="email">Email:</label>
                    <input type="email" id="email" placeholder="exemplo@email.com.br">
                </div>
            </div>
            <button @click="cadastrar">Cadastre-se</button>
            <router-link to="/"><button style="margin-top: 0.75rem">Voltar para login</button></router-link>
        </div>
    </div>
</template>

<script setup>
import { useRouter } from 'vue-router'

const router = useRouter()

async function cadastrar() {
    const matricula = document.getElementById('matricula').value;
    const senha = document.getElementById('senha').value;
    const confirmaSenha = document.getElementById('confirma-senha').value;
    const nomeCompleto = document.getElementById('nome-completo').value;
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