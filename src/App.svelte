<script>
  import CardList from "./components/CardList.svelte";

  let taskCards = [];
  let inProgressCards = [];
  let doneCards = [];
</script>

<main class="container is-fluid">
  <h1 class="is-size-3">Sveltdo</h1>
  <div class="columns">
    <CardList cards={taskCards} listName={"Tasks"} />
    <CardList cards={inProgressCards} listName={"In Progress"} />
    <CardList cards={doneCards} listName={"Done"} />
  </div>
</main>

<style>
</style>
