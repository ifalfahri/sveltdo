<script>
    import TodoCard from "./TodoCard.svelte";
    export let cards, listName

    let todo = ""

  function addTodo() {
    cards = [...cards, { todo, list: "Task"}]
  }
</script>

<div class="column is-4">
    <div class="card has-background-light">
      <div class="card-header">
        <p class="card-header-title">{listName}</p>
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