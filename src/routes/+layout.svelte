<script lang="ts">
  import "../app.css";
  let { children } = $props();

  import "@fontsource/inter";
</script>

{@render children()}

<style>
  :global(body) {
    font-family: "Inter", sans-serif;
  }
</style>
