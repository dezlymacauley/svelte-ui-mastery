<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<script lang="ts">
  import favicon from "$lib/assets/svelte_logo.svg";
  import "./page.css";
</script>

<style>
  /* 
    This is how you use rules (such as Tailwind classes) 
    from a `.css` file inside inside a Svelte style block.
    Technically this line is not needed here because I imported 
    the css file in the script tag.

    Normally that `import` line would not be in a `+page.svelte`,
    and would be in a `+layout.svelte`. 

    In that situation, the `@reference` line below below would be required
    to use `@apply` inside a Svelte style block.
  */
  @reference "./page.css";

  .outdoor-couple-container {
    /*  
      `@pply` is used to show that the style rules here are Tailwind classes
      and not regular css.
    */

    /* 
      Sets the background image 

      The reason this image can be used without any imports 
      is because it located at `static/images/outdoor_couple.png`
      You don't add the directory `static` because `/` already includes it.
    */
    @apply bg-[url(/images/outdoor_couple.png)];

    /*
      You need to set the height and width of the div or you won't see the
      background image.
    */
    /* @apply h-50 w-100; */
  }
</style>

<div class="outdoor-couple-container">
  <p>Hey</p>
</div>
