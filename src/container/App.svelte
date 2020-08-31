<script>
  import { onMount } from 'svelte'; 
  let data = []; 
  let characters = [];

  onMount( async() => {
    const response = await fetch('https://rickandmortyapi.com/api/character');
    data = await response.json();
    characters = data.results;
  });
</script>


<style>
  .characters {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    grid-gap: 8px;
  }

  figure,
  img{
      width: 100%;
      margin: 0;
  }

  figcaption{

  }
</style>

<div class="characters">
  {#each characters as character}
    <figure>
        <img src={character.image} alt={character.name}>
        <figcaption>{character.name}</figcaption>
    </figure>
  {:else}
    <p>Cargando...</p>
  {/each}
</div>
