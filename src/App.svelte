<script>
  import CardList from "./components/CardList.svelte";

  let taskCards = [];
  let inProgressCards = [];
  let doneCards = [];

  function handleEventAddTodo(event) {
    const { todo, listName } = event.detail;
    if (listName === "Tasks") {
      taskCards = [...taskCards, { todo }];
    } else if (listName === "In Progress") {
      inProgressCards = [...inProgressCards, { todo }];
    } else {
      doneCards = [...doneCards, { todo }];
    }
  }
</script>

<main class="container is-fluid">
  <h1 class="is-size-3">Sveltdo</h1>
  <div class="columns">
    <CardList cards={taskCards} listName={"Tasks"} on:addTodo={handleEventAddTodo} />
    <CardList cards={inProgressCards} listName={"In Progress"} on:addTodo={handleEventAddTodo}/>
    <CardList cards={doneCards} listName={"Done"} on:addTodo={handleEventAddTodo}/>
  </div>
</main>

<style>
</style>
