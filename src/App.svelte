<!-- App.svelte -->
<script>
  // Récupération du composant
  import PokeList from './components/PokeList.svelte'
let pokemons = []
  // On initialise la variable qui va contenir le Pokémon choisi
  let selectedPokemon = null

  const promise = getPokemons();

  async function getPokemons() {
    const res = await fetch('https://pokeapi.co/api/v2/pokemon');
    const json = await res.json();

    return json.results;
  }
   const handlePokemonSelect = (event) => {
      // Les données spécifique envoyé dans l'évènement seront
      // dans la propriété `detail`
      selectedPokemon = event.detail
    }
</script>

<h1>Pokédex</h1>
{#await promise}
  Chargement du Pokédex...
{:then pokemons}
  <PokeList pokemons={pokemons} on:selectPokemon={selectPokemon}  />

<!-- Si on a séléctionné un Pokémon, on peut afficher notre composant -->
  {#if selectedPokemon}
    <PokeDetails pokemon={selectedPokemon} />
<!-- Sinon, une indication -->
  {:else}
    Sélectionnez un Pokémon
  {/if}
{:catch error}
  Une erreur s'est produite : {error.message}
{/await}

