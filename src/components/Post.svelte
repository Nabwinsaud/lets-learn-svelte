<script lang="ts">
  import { onMount } from "svelte";
  let posts: Posts[] = [];
  onMount(async () => {
    const res = await fetch("https://jsonplaceholder.typicode.com/posts");
    posts = await res.json();
  });
</script>

<h6 class="text-slate-800 pb-3 border-b">Data Fetching in Svelte</h6>
<div
  class=" w-auto px-6 md:px-0 md:w-[800px] pt-3 h-auto grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-2"
>
  {#each posts.slice(0, 10) as post}
    <div class="border rounded-md py-3 my-1 space-y-2 px-2">
      <h6 class="text-sm">{post?.title}</h6>
    </div>
  {/each}
</div>
