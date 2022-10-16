<script lang="ts">
  import PS1 from "./components/PS1.svelte";

  let command:string = "";
  let commandsThatExists:string[] = ["ls","cv","help","cls"];
  let commandHistory:string[] = ["ls"];


  async function enterCommand(){
    if (commandsThatExists.includes(command)) {
      if(command === "cls"){
        commandHistory = [];
      } else {
        commandHistory.push(command);
      }
    } else {
      commandHistory.push("help");
    }
    //? Needed to tell the compiler the array has been updated: https://svelte.dev/tutorial/updating-arrays-and-objects
    commandHistory=commandHistory;
    
    command = "";

    //! Very important, this timer is necessary to waith sveltes re-render and the go to bottom
    await new Promise(r => setTimeout(r, 10));
    document.getElementById('scrollEnd').scrollIntoView({behavior: 'smooth'});
  }

</script>

<body id="body">

    {#each commandHistory as prevCommand}
    <PS1 executedCommand={prevCommand}/>
    {/each}
    
    <PS1 bind:command enterKey={enterCommand}/>
    <div id="scrollEnd"></div>
</body>

<style>
  body{
    scroll-behavior: smooth;
  }
</style>
