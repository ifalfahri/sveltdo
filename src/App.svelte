<script>
  import TodoCard from "./components/TodoCard.svelte";
  let cards = [
    "mY Content",
    "yur Content",
    "her Content",
  ]
</script>

<main class="container is-fluid">
  <h1 class="is-size-3">Sveltdo</h1>
  <div class="columns">
    <div class="column is-4">
      <div class="card has-background-light">
        <div class="card-header">
          <p class="card-header-title">Card</p>
        </div>
        <div class="card-content">
          {#each cards as card}
            <TodoCard content={card} />
          {/each}
        </div>
      </div>
    </div>
  </div>
</main>

<style>
</style>
