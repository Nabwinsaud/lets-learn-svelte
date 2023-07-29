<script lang="ts">
  import Todo from "./components/Todo.svelte";
  import Concepts from "./lib/Concepts.svelte";

  let name = "Coder";

  setTimeout(() => {
    name = `Nabin saud`;
  }, 2000);
</script>

<main class="flex flex-col justify-center items-center w-full h-screen text-xl">
  <h1>Learn the svelte concepts please</h1>

  <Concepts {name} age={20} hobbies={["code", "eat"]} />
  <Concepts name={"Ram"} age={19} hobbies={["Study", "Workout"]} />
  <Todo totalTodos={2000} />
</main>
