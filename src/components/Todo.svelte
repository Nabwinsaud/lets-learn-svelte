<script lang="ts">
  //  create the todos list of arrays  with unique uuid
  let todos = [
    { id: 1, text: "Learn Svelte", isCompleted: false },
    { id: 2, text: "Learn React", isCompleted: true },
    { id: 3, text: "Learn Rust", isCompleted: false },
    { id: 4, text: "Postgres", isCompleted: true },
  ];

  export let totalTodos = todos.length;
  let completedTodos = todos
    .filter((todo) => todo.isCompleted)
    .map((todo) => todo);
  // .map((todo) => todo);
  console.log("🚀 ~ file: Todo.svelte:13 ~ completedTodos:", completedTodos);
</script>

<h1>Completed todos is $ {JSON.stringify(completedTodos)}</h1>

<p class="my-2 py-2 text-slate-800 text-xl">total todo length : {totalTodos}</p>
