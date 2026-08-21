<script setup></script>

<template>
  <section>
    <div class="container">

      <div class="header-carteira">
        <h1>Carteira </h1>
        <span>digital</span>
      </div>

      <div class="bar-add">
        <form class="form">
          <input type="text" placeholder="R$">
          <input type="text" placeholder="Descrição">
          <button type="submit">Adicionar</button>
        </form>
      </div>

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
}

.header-carteira span {
  left: 90%;
  display: block;
  letter-spacing: 1.4px;
  color: #00000040;
}

.bar-add{
  margin: 1.5rem 0 0 0;
}

.form{
  display: flex;
  flex-direction: column;
  gap:10px;
}

.form input{
  padding: 10px 5px;
}

.form button{
  background-color: seagreen;
  color:white;
  border:0;
  border-radius: 5px;
  padding: 10px;
}
</style>
