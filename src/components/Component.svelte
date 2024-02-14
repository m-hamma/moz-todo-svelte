<script>
  export let nom;
  const panier = ['banane', 'fraise', 'poire', 'orange']
</script>

{#if nom}
  Bonjour {nom}
{/if}

<h1>Contenu du panier</h1>
<ul>
  {#each panier as fruit}
    <li>{fruit}</li>
  {/each}
</ul>