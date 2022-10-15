<script lang="ts">
  import Titulo from "./components/Titulo.svelte";
  import Usuario from "./components/Usuario.svelte";
  import type IUsuario from "./interfaces/IUsuario";

  let usuario: IUsuario | null = null;

  let valorImput = "";

  async function aoSubmeter() {
   const respostaUsuario = await fetch(`https://api.github.com/users/${valorImput}`);
   const dadosUsuario = await respostaUsuario.json();

   console.log(dadosUsuario);
   
    /*   usuario = {
        login: "anaoliveira001",
        avatar_url: "https://github.com/anaoliveira001.png",
        perfil_url: "https://github.com/anaoliveira001",
        nome: "Ana Paula Oliveira",
        repositorios_publicos: 20,
        seguidores: 10,
    }; */
  }
</script>

<div class="app">
  <header>
    <Titulo />
    <div class="busca-usuario">
      <form on:submit|preventDefault={aoSubmeter}>
        <input type="text" class="input" bind:value={valorImput} placeholder="Find a Github user" />

        <div class="button-container">
          <button type="submit" class="button">Search</button>
        </div>
      </form>
    </div>
  </header>

  {#if usuario}
    <Usuario {usuario} />
  {/if}
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

  .input {
    padding: 15px 25px;
    width: calc(100% - 8.75rem);
    font-size: 1rem;
    border-radius: 8px;
    border: 1px solid #0e0f12;
    box-shadow: 0px 17px 52px rgba(222, 231, 247, 0.4);
    outline: 0;
  }

  .input::placeholder {
    font-family: "Roboto";
    font-style: italic;
    font-weight: 300;
    font-size: 19.5px;
    line-height: 26px;
    color: #6e8cba;
  }

  .button-container {
    position: absolute;
    width: 9.625rem;
    right: 0;
    top: 0;
    bottom: 0;
    display: flex;
  }

  .button {
    padding: 15px 24px;
    border-radius: 8px;
    border: none;
    background: #cea4de;
    line-height: 26px;
    color: #fff;
    font-size: 22px;
    cursor: pointer;

    transition: background-color 0.2s;

    display: flex;
    align-items: center;
    gap: 13px;
  }

  .button:hover {
    background: #000000;
  }

  
</style>
