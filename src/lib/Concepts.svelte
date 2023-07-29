<script lang="ts">
  export let name = "Nabin";
  export let age = 19;
  export const isMarried = false; //*  remeber const is immutable in out of parent svelte component
  export let hobbies = ["Coding", "Reading", "Gaming"];
</script>

<h1>Hello {name}</h1>

<h6 class="text-slate-700 my-2 py-1">hobbies: {hobbies}</h6>
<h6 class="text-slate-800 my-2 py-1 text-xl">Age: {age}</h6>
