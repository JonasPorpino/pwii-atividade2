<template>
  <main class="principal">
  <div id="app">
    <b-navbar toggleable="lg" type="dark" variant="dark">
      <b-navbar-brand href="#">Agenda de Contatos</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item to="/">Lista de Contatos</b-nav-item>
          <b-nav-item to="/form">Criar Contato</b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>

    <router-view />
  </div>
  <p> <br> </p>
  </main>
</template>

<style>
  .principal{
    text-align: center;
    background: #cbd2e2;
    margin: 10% 10%;
    box-shadow: 5px 3px 7px 1px #5c5c5c;
    border-radius: 10px;
  }
</style>
