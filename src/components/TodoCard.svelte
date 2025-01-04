<script>
  import { createEventDispatcher } from "svelte";
  export let content, listName, index;

  const dispatch = createEventDispatcher();

  function handleDeleteTodo() {
    dispatch("deleteTodo", { index, listName });
  }
  function handleMoveRight() {
    dispatch("moveRight", { index, listName });
  }
    function handleMoveLeft() {
        dispatch("moveLeft", { index, listName });
    }
</script>

<div class="card mb-3 has-background-primary-light">
  <div class="card-content">
    <div class="columns is-mobile">
      <div class="column is-narrow">
        {#if listName !== "Tasks"}
          <span class="icon has-text-primary" on:click={handleMoveLeft}>
            <i class="fa fa-chevron-left"></i>
          </span>
        {/if}
      </div>
      <div class="column">
        <p class="has-text-primary-dark">{content}</p>
      </div>
      <div class="column is-narrow">
        <span class="icon has-text-danger" on:click={handleDeleteTodo}>
          <i class="fa fa-trash"></i>
        </span>
      </div>
      <div class="column is-narrow">
        {#if listName !== "Done"}
          <span class="icon has-text-primary" on:click={handleMoveRight}>
            <i class="fa fa-chevron-right"></i>
          </span>
        {/if}
      </div>
    </div>
  </div>
</div>
