<script lang="ts">
  import Formulario from './components/Formulario.svelte';
  import Titulo from "./components/Titulo.svelte";
  import Usuario from './components/Usuario.svelte';
  import type IUsuario from "./interfaces/IUsuario";

  let usuario: IUsuario | null = null;

  function definirUsuario(evento: CustomEvent<IUsuario | null>) {
    usuario = evento.detail;
  }
</script>

<div class="app">
  <header>
    <Titulo />

    <div class="busca-usuario">
      <Formulario on:aoAlterarUsuario={definirUsuario} />
    </div>
  </header>

  {#if usuario}
    <Usuario {usuario} />
  {/if}
</div>
<div class="footer">
  Svelte aplication - GitHub Profiles <br>
  For the full functionality of this application, a public API from GitHub - <span class="api">https://api.github.com/users/username</span>  - was used.
</div>
<style>
  .app {
    max-height: 100vh;
  }

  header {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .busca-usuario {
    position: relative;
    width: 70%;
  }

.footer{
  font-family:monospace;
  text-align: center;
  padding: 15rem;
}

.api{
  font-family:monospace;
  color: blueviolet;
  font-weight: bold;
}

.api:hover{
  color: cadetblue;
}
</style>