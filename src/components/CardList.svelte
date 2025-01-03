<script>
  import { createEventDispatcher } from "svelte";
  import TodoCard from "./TodoCard.svelte";
  export let cards, listName;

  const dispatch = createEventDispatcher();

  let todo = "";

  function addTodo() {
    dispatch("addTodo", { todo, listName });
  }
</script>

<div class="column is-4">
  <div class="card has-background-light">
    <div class="card-header">
      <p class="card-header-title">{listName}</p>
    </div>
    <div class="card-content">
      {#each cards as card}
        <TodoCard content={card.todo} listName={listName} />
      {/each}
      <input type="text" class="input is-primary mb-2" bind:value={todo} />
      <button on:click={addTodo} class="button is-primary">Add</button>
    </div>
  </div>
</div>
