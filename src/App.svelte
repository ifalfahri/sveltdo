<script>
  import CardList from "./components/CardList.svelte"

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
</script>

<main class="container is-fluid">
  <h1 class="is-size-3">Sveltdo</h1>
  <div class="columns">
    <CardList cards={cards} />
  </div>
</main>

<style>
</style>
