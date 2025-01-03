<script>
  import TodoCard from "./components/TodoCard.svelte";
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
          <TodoCard content={'mY Content'} />
          <TodoCard content={'yur Content'} />
          <TodoCard content={'her Content'} />
        </div>
      </div>
    </div>
  </div>
</main>

<style>
</style>
