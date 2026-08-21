<script setup>
import '../styles/carteira.css';
import { ref, computed } from 'vue';

const valor = ref(0);
const descricao = ref('');
const tipo = ref('');

const dadosContas = ref([]);

const validarCampos = () => {
  if (descricao.value.trim() === "" || tipo.value.trim() === "") {
    alert("Campos obrigatórios");
    return;
  }

  dadosContas.value.push({
    id: Date.now(),
    valor: Number(valor.value),
    descricao: descricao.value,
    tipo: tipo.value
  });

  // Limpa os campos após adicionar
  valor.value = 0;
  descricao.value = '';
  tipo.value = '';
}

const remover = (id) => {
  if (confirm("Deseja excluir?")) {
    dadosContas.value = dadosContas.value.filter(item => item.id !== id);
  }
}

const totalRenda = computed(() => {
  return dadosContas.value
    .filter(item => item.tipo === 'Renda')
    .reduce((acumulador, item) => acumulador + Number(item.valor), 0);
});

// Corrigido 'Gastos' para 'gastos'
const totalGastos = computed(() => {
  return dadosContas.value
    .filter(item => item.tipo === 'gastos')
    .reduce((acumulador, item) => acumulador + Number(item.valor), 0);
});

// Corrigido computer para computed
const saldoTotal = computed(() => {
  return totalRenda.value - totalGastos.value;
});


const moedaBrasileira = (valor) => {
  return new Intl.NumberFormat('pt-BR', {
    style: 'currency',
    currency: 'BRL'
  }).format(valor);
}


</script>

<template>
  <section>
    <div class="container">

      <div class="header-carteira">
        <h1>Carteira </h1>
        <span>digital</span>
      </div>

      <div class="header-saldo">
        <div class="the-saldo">
          <span class="title-saldo">Saldo</span>

          <p> {{ moedaBrasileira(saldoTotal) }}</p>
        </div>
        <div class="the-gastos">
          <span class="title-gastos">Gastos</span>
          <p>{{ moedaBrasileira(totalGastos) }}</p>
        </div>
      </div>

      <div class="bar-add">
        <form class="form" @submit.prevent="validarCampos">
          <input type="number" placeholder="R$" v-model="valor">
          <input type="text" placeholder="Descrição" v-model="descricao" class="description">
          <select class="tipo" v-model="tipo">
            <option value="">Selecione tipo</option>
            <option value="gastos">Gastos</option>
            <option value="Renda">Renda</option>
          </select>
          <button type="submit">Adicionar</button>
        </form>
      </div>

      <ul class="lista-contas">
        <li v-for="itemLista in dadosContas" :key="itemLista.id">
          <h3> {{moedaBrasileira(itemLista.valor )}}</h3>
          <div>
            <h4 class="description">{{ itemLista.descricao }}</h4>
            <span>{{ itemLista.tipo }}</span>
          </div>
          <button @click="remover(itemLista.id)">X</button>
        </li>
      </ul>

    </div>
  </section>
</template>