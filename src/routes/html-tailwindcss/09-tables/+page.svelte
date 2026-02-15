<script lang="ts">
  import favicon from "$lib/svg/svelte_logo.svg";
  import "$lib/css/default.css"
</script>

<svelte:head>
  <link rel="icon" href={favicon} />
</svelte:head>

<style>
  @reference "$lib/css/default.css";
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
