<script lang="ts">
  import Box from "./components/Box.svelte";
  import Post from "./components/Post.svelte";
  import Todo from "./components/Todo.svelte";
  import Concepts from "./lib/Concepts.svelte";

  let name = "Coder";

  let paragraphTag = `<p>Hello i am sanitized paragraph</p>`;

  setTimeout(() => {
    name = `Nabin saud`;
  }, 2000);
</script>

<main
  class="flex my-6 pt-4 flex-col justify-center items-center w-full h-screen text-xl"
>
  <div class="my-6">
    <h1 class="my-6">Learn the svelte concepts please</h1>
  </div>

  <Concepts {name} age={20} hobbies={["code", "eat"]} />
  <Concepts name={"Ram"} age={19} hobbies={["Study", "Workout"]} />
  <Todo />
  <Post />

  <!-- slots in svelte -->
  <Box>
    <h1 class="text-md">Hello the fudament of slot</h1>
    <p class="text-sm">
      it is smiliar like children in react where we can render jsx or React Node
      as types
    </p>
  </Box>

  <!-- sanitization  -->

  {@html paragraphTag}
</main>
