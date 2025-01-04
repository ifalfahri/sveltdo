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
  function handleEventDeleteTodo(event) {
    const { index, listName } = event.detail;
    if (listName === "Tasks") {
      taskCards.splice(index, 1);
      taskCards = [...taskCards];
    } else if (listName === "In Progress") {
      inProgressCards.splice(index, 1);
      inProgressCards = [...inProgressCards];
    } else {
      doneCards.splice(index, 1);
      doneCards = [...doneCards];
    }
  }
  function handleEventMoveRight(event) {
    const { index, listName } = event.detail;
    if (listName === "Tasks") {
      let todo = taskCards.splice(index, 1)
      inProgressCards = [...inProgressCards, todo[0]];
      taskCards = [...taskCards];
    } else if (listName === "In Progress") {
      let todo = inProgressCards.splice(index, 1)
      doneCards = [...doneCards, todo[0]];
      inProgressCards = [...inProgressCards];
    }
  }
  function handleEventMoveLeft(event) {
    const { index, listName } = event.detail;
    if (listName === "In Progress") {
      let todo = inProgressCards.splice(index, 1)
      taskCards = [...taskCards, todo[0]];
      inProgressCards = [...inProgressCards];
    } else if (listName === "Done") {
      let todo = doneCards.splice(index, 1)
      inProgressCards = [...inProgressCards, todo[0]];
      doneCards = [...doneCards];
    }
  }

</script>

<main class="container is-fluid">
  <h1 class="is-size-3">Sveltdo</h1>
  <div class="columns">
    <CardList
      cards={taskCards}
      listName={"Tasks"}
      on:addTodo={handleEventAddTodo}
      on:deleteTodo={handleEventDeleteTodo}
      on:moveRight={handleEventMoveRight}
    />
    <CardList
      cards={inProgressCards}
      listName={"In Progress"}
      on:addTodo={handleEventAddTodo}
      on:deleteTodo={handleEventDeleteTodo}
      on:moveRight={handleEventMoveRight}
      on:moveLeft={handleEventMoveLeft}
    />
    <CardList
      cards={doneCards}
      listName={"Done"}
      on:addTodo={handleEventAddTodo}
      on:deleteTodo={handleEventDeleteTodo}
      on:moveLeft={handleEventMoveLeft}
    />
  </div>
</main>

<style>
</style>
