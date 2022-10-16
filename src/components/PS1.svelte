<script lang="ts">
    //? Output components
    import LS from "./LS.svelte";
    import Help from "./Help.svelte";
    import CV from "./CV.svelte";

    //* Parent
    export let enterKey = () => {};
    export let command:string = "";
    export let executedCommand:string = "";

    //* Own functions
    const ps1:string = "web-page@yuki#";

    async function handleInputKeyPress(event){
        //? Manages input width 
        document.getElementById("commandInput").style.width = (command.length * 0.5) + "em";

        //? Solves android virtual keyboard bug
        let code = event.target.value.charAt(event.target.selectionStart - 1).charCodeAt();
        command = command;

        //? Handles keyboard input, any other input wont do nothing
        switch (event.keyCode) {
            // Enter
            case 13:
                document.getElementById("commandInput").style.width = 0 + "em";
                enterKey();
                break;
        }
    }

</script>

<style>
    div{
        display: flex;
        align-items:flex-start;
        width: 100%;
        font-size: 1.5em;
    }
    .cursor{
        padding-top: 2px;
        animation: blinker 1s linear infinite;
    }
    @keyframes blinker {
        50% {
            opacity: 0;
        }
    }
    input{
        background: transparent;
        caret-color: transparent;
        border: none;
        font-family: inherit;
        font-family: 2em;
        font-size: 1em;
        color: inherit;
        outline: none;
        width: 0.1em;
    }
</style>

<svelte:window/> 

{#if executedCommand !== ""}
    <div>
        <p>{`${ps1} ${executedCommand}`}</p>
    </div>
    {#if executedCommand === "ls"}
        <LS/>
    {:else if executedCommand === "help"}
        <Help/>
    {:else if executedCommand === "cv"}
        <CV/>
    {/if}
{:else}
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <div on:click={() => document.getElementById("commandInput").focus()}>
        <!-- svelte-ignore a11y-autofocus -->
        <p>{ps1} <input type="text" id="commandInput" bind:value={command} on:keyup={handleInputKeyPress} autocorrect="off" autocapitalize="off" autofocus><span class="cursor">_</span></p>
    </div>
{/if}

