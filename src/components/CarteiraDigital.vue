<script setup></script>

<template>
  <section>
    <div class="container">

      <div class="header-carteira">
        <h1>Carteira </h1>
        <span>digital</span>
      </div>

      <div class="header-saldo">
        <div class="the-saldo">
          <span>Saldo</span>
          <p>R$ 1520,00</p>
        </div>
        <div class="the-gastos">
          <span>Gastos</span>
          <p>R$ 20,00</p>
        </div>
      </div>

      <div class="bar-add">
        <form class="form">
          <input type="text" placeholder="R$">
          <input type="text" placeholder="Descrição">
          <button type="submit">Adicionar</button>
        </form>
      </div>

      <ul class="lista-contas">
        <li>
          <h3>R$ 20,00</h3>
          <div>
            <h4>Arroz</h4>
            <span>alimentação</span>
          </div>
          <button>X</button>

        </li>

        <li>
          <h3>R$ 1500,00</h3>
          <div>
            <h4>Notebook</h4>
            <span>compras</span>
          </div>
          <button>X</button>
        </li>
      </ul>

    </div>
  </section>
</template>

<style scoped>
.container {
  padding: 45px;
  max-width: 450px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 25px;
}

.header-carteira span {
  left: 90%;
  display: block;
  letter-spacing: 1.4px;
  color: #00000040;
}

.header-saldo{
  display: flex;
  gap:50px;
}

.the-saldo, .the-gastos{
  border:1px solid #ccc;
  padding: .5rem;
}

.bar-add {
  margin: 1.5rem 0 0 0;
}

.form {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.form input {
  padding: 10px 5px;
}

.form button {
  background-color: seagreen;
  color: white;
  border: 0;
  border-radius: 5px;
  padding: 10px;
}

.lista-contas li{
  display: grid;
  grid-template-columns: 150px auto 40px;
  gap:10px;
  align-items: center;
  padding:10px 0;
  border-bottom: 1px saddlebrown solid;
}

.lista-contas li span{
  font-size: 13px;
}

.lista-contas button{
  background-color: tomato;
  color: white;
  cursor: pointer;
  border: 0;
  border-radius: 5px;
  padding: 10px 0px;
}
</style>
