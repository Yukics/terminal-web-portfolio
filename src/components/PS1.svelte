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

    function handleInputKeyPress(event){
        //? Manages default width 
        const inputWidth: string = document.getElementById("commandInput").style.width;
        let inputNumber: number = parseFloat(inputWidth.slice(0, -2));
        if(inputWidth === ""){
            inputNumber = 0;
        }

        //? Handles keyboard input, any other input wont do nothing
        switch (true) {
            // Backspace && Delete 
            case (event.which === 8 || event.which === 46):
                document.getElementById("commandInput").style.width = (inputNumber - 0.5) + "em";  
                break;
            // Enter
            case (event.which === 13):
                document.getElementById("commandInput").style.width = 0 + "em";
                enterKey();
                break;
            // Numbers && characters
            case (event.which >= 48 && event.which <= 90):
                document.getElementById("commandInput").style.width = (inputNumber + 0.5) + "em";
                break;
            default:
                event.preventDefault();
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
        width: 0em;
    }
</style>

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
        <p>{ps1} <input type="text" id="commandInput" bind:value={command} autocorrect="off" autocapitalize="off" on:keydown={handleInputKeyPress} autofocus><span class="cursor">_</span></p>
    </div>
{/if}


