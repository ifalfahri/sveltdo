<script>
  import TodoCard from "./components/TodoCard.svelte";

  let cards = [
    {
      todo: "mY Content",
      list: "Task"
    },
    {
      todo: "yur Content",
      list: "Task"
    },
    {
      todo: "her Content",
      list: "Task"
    },
  ]

  let todo = ""

  function addTodo() {
    cards = [...cards, { todo, list: "Task"}]
  }
</script>

<main class="container is-fluid">
  <h1 class="is-size-3">Sveltdo</h1>
  <div class="columns">
    <div class="column is-4">
      <div class="card has-background-light">
        <div class="card-header">
          <p class="card-header-title">Tasks</p>
        </div>
        <div class="card-content">
          {#each cards as card}
            <TodoCard content={card.todo} />
          {/each}
          <input type="text" class="input is-primary mb-2" bind:value={todo}/>
          <button on:click={addTodo} class="button is-primary">Add</button>
        </div>
      </div>
    </div>
  </div>
</main>

<style>
</style>
