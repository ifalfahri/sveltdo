<script>
  import CardList from "./components/CardList.svelte";

  let taskCardsLocal = JSON.parse(localStorage.getItem("taskCards"));
  let inProgressCardsLocal = JSON.parse(localStorage.getItem("inProgressCards"));
  let doneCardsLocal = JSON.parse(localStorage.getItem("doneCards"));

  let taskCards = taskCardsLocal ? taskCardsLocal : [];
  let inProgressCards = inProgressCardsLocal ? inProgressCardsLocal : [];
  let doneCards = doneCardsLocal ? doneCardsLocal : [];

  function handleEventAddTodo(event) {
    const { todo, listName } = event.detail;
    if (listName === "Tasks") {
      taskCards = [...taskCards, { todo }];
      localStorage.setItem("taskCards", JSON.stringify(taskCards));
    } else if (listName === "In Progress") {
      inProgressCards = [...inProgressCards, { todo }];
      localStorage.setItem("inProgressCards", JSON.stringify(inProgressCards));
    } else {
      doneCards = [...doneCards, { todo }];
      localStorage.setItem("doneCards", JSON.stringify(doneCards));
    }
  }
  function handleEventDeleteTodo(event) {
    const { index, listName } = event.detail;
    if (listName === "Tasks") {
      taskCards.splice(index, 1);
      taskCards = [...taskCards];
      localStorage.setItem("taskCards", JSON.stringify(taskCards));
    } else if (listName === "In Progress") {
      inProgressCards.splice(index, 1);
      inProgressCards = [...inProgressCards];
      localStorage.setItem("inProgressCards", JSON.stringify(inProgressCards));
    } else {
      doneCards.splice(index, 1);
      doneCards = [...doneCards];
      localStorage.setItem("doneCards", JSON.stringify(doneCards));
    }
  }
  function handleEventMoveRight(event) {
    const { index, listName } = event.detail;
    if (listName === "Tasks") {
      let todo = taskCards.splice(index, 1)
      inProgressCards = [...inProgressCards, todo[0]];
      taskCards = [...taskCards];
      localStorage.setItem("taskCards", JSON.stringify(taskCards));
      localStorage.setItem("inProgressCards", JSON.stringify(inProgressCards));
    } else if (listName === "In Progress") {
      let todo = inProgressCards.splice(index, 1)
      doneCards = [...doneCards, todo[0]];
      inProgressCards = [...inProgressCards];
      localStorage.setItem("inProgressCards", JSON.stringify(inProgressCards));
      localStorage.setItem("doneCards", JSON.stringify(doneCards));
    }
  }
  function handleEventMoveLeft(event) {
    const { index, listName } = event.detail;
    if (listName === "In Progress") {
      let todo = inProgressCards.splice(index, 1)
      taskCards = [...taskCards, todo[0]];
      inProgressCards = [...inProgressCards];
      localStorage.setItem("taskCards", JSON.stringify(taskCards));
      localStorage.setItem("inProgressCards", JSON.stringify(inProgressCards));
    } else if (listName === "Done") {
      let todo = doneCards.splice(index, 1)
      inProgressCards = [...inProgressCards, todo[0]];
      doneCards = [...doneCards];
      localStorage.setItem("inProgressCards", JSON.stringify(inProgressCards));
      localStorage.setItem("doneCards", JSON.stringify(doneCards));
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
