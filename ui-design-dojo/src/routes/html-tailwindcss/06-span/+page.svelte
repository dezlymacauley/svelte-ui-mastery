<script lang="ts">
  import favicon from "$lib/assets/svelte_logo.svg";
  import "./page.css";
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<!--
  The `span` html element is an inline element.

  1. Inline elements will ignore any width or height properties
  that you set on them.

  2. The height and width of an inline element is dependent on the size 
  of the content inside its tag.
-->
<span class="text-white border-2 border-green-500">Message A</span>
<span class="text-white border-2 border-pink-500">Message B</span>
