<script lang="ts">
  import PS1 from "./components/PS1.svelte";
  import LS from "./components/LS.svelte";
  let command:string = "";

  function enterCommand(){
    console.log(command)
  }
  function catCV(){
        // TODO Print my cv
    }
  function catContact(){
      // TODO Print my cv
  }
</script>

<body>
  <PS1 executedCommand={"ls"}/>
  <LS catCV={catCV()} catContact={catContact()}/>
  <PS1 bind:command enterKey={enterCommand}/>
  <!-- <h1>IT IS: {command}</h1> -->
</body>

<style>
</style>
