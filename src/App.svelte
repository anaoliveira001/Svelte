<script lang="ts">

  import BarraSuperior from "./components/BarraSuperior.svelte";
import Titulo from "./components/Titulo.svelte";
  import Usuario from "./components/Usuario.svelte";

  let valorImput = 'Svelte';

  function aoSubmeter(){
	console.log(valorImput);
  }
</script>

	<div class="app">
		<header>
			<Titulo />
			<div class="busca-usuario">
				<form on:submit|preventDefault={aoSubmeter}>
					<input type="text" class="input" bind:value={valorImput}>

					<div class="button-container">
						<button type="submit" class="button">Search</button>
					</div>

				</form>
			</div>
		</header>

	<div class="card-usuario">
			<BarraSuperior />

			<div class="usuario">
				<Usuario />
			</div>
		</div>
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

  .card-usuario {
    margin-top: 65px;
  }

  .usuario {
    padding: 28px 0;
    background: rgba(255, 255, 255, 0.5);
    box-shadow: -12px 37px 45px rgba(133, 127, 201, 0.18);
    border-radius: 0px 0px 13px 13px;

    display: flex;
    justify-content: center;
  }

</style>
