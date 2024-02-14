<!-- PokeList.svelte -->
<script>
  // On récupère en propriété le tableau des Pokémons
  // et on lui donne [] comme valeur par défaut.
  export let pokemons = []
  const handlePokemonClick = (pokemon) => {
            // Ici on récupère bien le Pokémon sur lequel on a cliqué
            console.log(pokemon)
          }
  import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();




</script>

<ul>
  {#each pokemons as pokemon}
  <li>
    {pokemon.name}
  </li>
  <button on:click="{() => handlePokemonClick(pokemon)}" >
      {pokemon.name}
    </button>

  {/each}

</ul>

