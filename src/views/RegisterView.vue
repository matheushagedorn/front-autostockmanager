<template>
    <div class="login">
        <div class="login-container">
            <img src="/src/assets/img/car.png" alt="Carro">
            <h1>AutoStock Manager</h1>

            <div class="login-container-form">
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
                <button @click="cadastrar">Cadastre-se</button>
                <router-link to="/"><button style="margin-top: 0.75rem">Voltar para login</button></router-link>
            </div>
        </div>
    </div>
</template>

<script setup>
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

    const response = await fetch('localhost:8080/cadastrar-usuario', { // atualizar para link da api
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
        },
        body: JSON.stringify({
            modelo: 'Fusca',
            marca: 'Volkswagen',
            cor: 'Preto',
            ano: 1970,
            quilometragem: 100000,
            valor_revenda: 10000,
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