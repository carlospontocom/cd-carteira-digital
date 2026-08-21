<script setup>
  import '../styles/carteira.css';
  import { ref } from 'vue';
  const valor = ref('');
  const descricao = ref('');
  const tipo = ref('');

  const dadosContas = ref([]);

  const validarCampos = () =>{
    if(valor.value.trim()==="" || descricao.value.trim()===""){
      alert("Campos obrigatórios");
      return;
    }
     dadosContas.value.push({
      id:Date.now(),
      valor:valor.value,
      descricao:descricao.value,
      tipo: tipo.value
     })
  }


  const remover=(id)=>{
    if(confirm("Deseja excluir?")){
      dadosContas.value = dadosContas.value.filter(item => item.id !== id);
    }
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
          <p>R$ 1520,00</p>
        </div>
        <div class="the-gastos">
          <span class="title-gastos">Gastos</span>
          <p>R$ 20,00</p>
        </div>
      </div>

      <div class="bar-add">
        <form class="form" @submit.prevent="validarCampos">
          <input type="text" placeholder="R$" v-model="valor">
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
          <h3>R$ {{ itemLista.valor }}</h3>
          <div>
            <h4 class="description">{{itemLista.descricao}}</h4>
            <span>{{ itemLista.tipo}}</span>
          </div>
          <button @click="remover(itemLista.id)">X</button>
        </li> 
      </ul>

    </div>
  </section>
</template>
