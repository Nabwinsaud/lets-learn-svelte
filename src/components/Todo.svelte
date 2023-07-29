<script lang="ts">
  let todos = [
    { id: 1, text: "Learn Svelte", isCompleted: false },
    { id: 2, text: "Learn React", isCompleted: true },
    { id: 3, text: "Learn Rust", isCompleted: false },
    { id: 4, text: "Learn Postgres", isCompleted: true },
  ];

  let todoInput = "";
  $: console.log("🚀 ~ file: Todo.svelte:10 ~ todoInput:", todoInput);
  // i love svelete reactive state game chnaging
  //   export let totalTodos = todos.length;
  $: totalTodos = todos.length;
  $: completedTodos = todos.filter((todo) => todo.isCompleted).length;

  const removeTodo = (index: number) => {
    todos = todos.filter((t) => t.id !== index);
  };

  let todoId: number;

  $: console.log("toodo id is", todoId);
  $: {
    if (totalTodos === 0) {
      todoId = 1;
    } else {
      todoId = Math.max(...todos.map((t) => t.id)) + 1;
    }
  }
  const addTodo = () => {
    // todos.push({ id: todos.length + 1, text: todoInput, isCompleted: false });
    todos = [...todos, { id: todoId, text: todoInput, isCompleted: false }];
    todoInput = "";
  };
</script>

<h1>Completed todos is {completedTodos} out of {totalTodos}</h1>

<p class="my-2 py-2 text-slate-800 text-xl">total todo length : {totalTodos}</p>

<div class="my-6 py-2 space-y-6">
  <!-- below type saftey is getting worse ohh -->
  <form on:submit|preventDefault={addTodo}>
    <div class="gap-6 flex items-center">
      <input
        bind:value={todoInput}
        on:keydown={(e) => (todoInput = e.target.value)}
        type="text"
        placeholder="Enter todo name"
        class="rounded-md py-2 px-6 border outline-none focus:border-purple-500"
      />
    </div>
  </form>

  {#each todos as todo}
    <div class="flex items-center gap-6">
      <div
        class="flex border py-2 rounded-md px-1 justify-between gap-3 w-full"
      >
        <div class="flex gap-3">
          <input
            on:click={() => (todo.isCompleted = !todo.isCompleted)}
            id="todo-{todo.id}"
            checked={todo.isCompleted}
            type="checkbox"
          />
          <h1 class="text-md text-bold">{todo.text}</h1>
        </div>
        <div>
          <button
            class="rounded-md px-2 py-1 text-sm bg-black text-white"
            on:click={() => removeTodo(todo.id)}>Delete</button
          >
        </div>
      </div>
    </div>
  {:else}
    <h1>Not thing to show here</h1>
  {/each}
</div>
