<script lang="ts">
  import NavBar from "./components/NavBar.svelte"
  import Main from "./components/Main.svelte"
  let page:string = "/";
</script>

<body>
  <NavBar bind:index={page}/>
  <Main bind:index={page}/>
</body>

<style>
</style>
