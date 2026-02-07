<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<script lang="ts">
  import favicon from "$lib/assets/svelte_logo.svg";
  import "./page.css";
</script>

<style>
  @reference "./page.css";
</style>

<!---------------------------------------------------------------------------->

<table>

  <thead>
    <tr>
      <th>State</th>
      <th>City</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>Indiana</td>
      <td>Indianapolis</td>
    </tr>
    <tr>
      <td>Ohio</td>
      <td>Columbus</td>
    </tr>
    <tr>
      <td>Michigan</td>
      <td>Detroit</td>
    </tr>
  </tbody>
</table>

<!---------------------------------------------------------------------------->
