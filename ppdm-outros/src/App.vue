<script setup>
import { ref } from 'vue'

const produtos = ref([
  {
    nome: 'Notebook',
    descricao: 'Notebook com 8GB de RAM e SSD de 256GB.',
    preco: 3500
  },
  {
    nome: 'Smartphone',
    descricao: 'Smartphone com câmera de alta resolução e 128GB de armazenamento.',
    preco: 2200
  }
])

const nome = ref('')
const descricao = ref('')
const preco = ref('')

function cadastrarProduto() {
  if (!nome.value || !descricao.value || !preco.value) {
    alert('Preencha todos os campos.')
    return
  }

  produtos.value.push({
    nome: nome.value,
    descricao: descricao.value,
    preco: Number(preco.value)
  })

  // Limpa os campos após o cadastro
  nome.value = ''
  descricao.value = ''
  preco.value = ''
}
</script>

<template>
  <div class="container">
    <h1>Lista de Produtos</h1>

    <div class="formulario">
      <h2>Cadastrar Produto</h2>

      <input
        v-model="nome"
        type="text"
        placeholder="Nome do produto"
      />

      <input
        v-model="descricao"
        type="text"
        placeholder="Descrição do produto"
      />

      <input
        v-model="preco"
        type="number"
        step="0.01"
        placeholder="Preço"
      />

      <button @click="cadastrarProduto">
        Cadastrar
      </button>
    </div>

    <div class="lista">
      <h2>Produtos cadastrados</h2>

      <div
        v-for="(produto, index) in produtos"
        :key="index"
        class="produto"
      >
        <h3>{{ produto.nome }}</h3>
        <p>{{ produto.descricao }}</p>
        <strong>
          R$ {{ produto.preco.toFixed(2).replace('.', ',') }}
        </strong>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 800px;
  margin: 40px auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}

h1 {
  text-align: center;
  color: #333;
}

.formulario {
  display: flex;
  flex-direction: column;
  gap: 12px;
  padding: 20px;
  margin-bottom: 30px;
  background-color: #f5f5f5;
  border-radius: 8px;
}

.formulario h2,
.lista h2 {
  margin-top: 0;
}

input {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 16px;
}

button {
  padding: 10px;
  border: none;
  border-radius: 5px;
  background-color: #42b883;
  color: white;
  font-size: 16px;
  cursor: pointer;
}

button:hover {
  background-color: #36966d;
}

.produto {
  padding: 15px;
  margin-bottom: 15px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background-color: white;
}

.produto h3 {
  margin-top: 0;
  color: #42b883;
}

.produto p {
  color: #555;
}

.produto strong {
  font-size: 18px;
}
</style>
