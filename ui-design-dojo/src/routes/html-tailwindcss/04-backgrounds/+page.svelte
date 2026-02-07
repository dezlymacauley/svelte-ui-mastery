<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<script lang="ts">
  import favicon from "$lib/assets/svelte_logo.svg";
  import "./page.css";
</script>

<style>
  /* 
    `@reference` is :required to use the rules of a .css file,
    inside a Svelte style block.
  
    Without this line you will get an error if you try to use
    `@apply`
  */
  @reference "./page.css";

  .info-text {
    /* 
      `@pply` is used to show that you are setting style rules that 
      are Tailwind classes and not regular CSS.
    */
    @apply bg-purple-800 text-white;
  }

  .outdoor-couple-container1 {
    /*  
    */

    /*
      You need to set the height and width of the div or you won't see the
      background image.

      I've added a purple border to make it easier to see 
      the location of the div.

      Note: This setting alone only controls the height and width 
      of the container. If the background image is larger the majority of
      the image won't be visible.
    */
    @apply h-50 w-100;
    @apply border-4 border-purple-600;


    /* 
      Set the background image:

      The reason this image can be used without any imports 
      is because it located at `static/images/outdoor_couple.png`
      You don't add the directory `static` because `/` already includes it.
    */
    @apply bg-[url(/images/outdoor_couple.png)];
  }

  .outdoor-couple-container2 {
    @apply h-50 w-100;
    @apply border-4 border-amber-600;
    @apply bg-[url(/images/outdoor_couple.png)];
    
    /* 
      This will scale the image and attempt to make it fit within
      the container. Some parts of the image may be cropped.
    */
    @apply bg-cover;

  }

  .outdoor-couple-container3 {
    @apply h-50 w-100;
    @apply border-4 border-pink-600;
    @apply bg-[url(/images/outdoor_couple.png)];


    /*  
      Use `bg-contain` when you want to make sure that the image is not cropped
      if it is larger than the height and width of the container.

      However bg-contain will repeat the image to fill 
      any leftover space in the div.

      You can overide this default behavior with the class `bg-no-repeat`
    */
    @apply bg-contain bg-no-repeat bg-center;
  }

  .outdoor-couple-container4 {
    @apply h-50 w-100;
    @apply border-4 border-green-500;
    @apply bg-[url(/images/outdoor_couple.png)];
    @apply bg-contain;
  }
</style>



<div class="outdoor-couple-container1">
  <span class="info-text">No image adjustment</span>
</div>

<div class="outdoor-couple-container2">
  <span class="info-text">bg-cover</span>
</div>

<div class="outdoor-couple-container3">
  <span class="info-text">bg-contain with no-repeat and bg-center</span>
</div>

<div class="outdoor-couple-container4">
  <span class="info-text">bg-contain with repeat</span>
</div>
