<script lang="ts">
    //? Example 
    // export let index:string;
</script>

<div>
    <div class="main">
        <!-- <p on:click={catCV} class="file" href="/">.portfolio</p> -->
        <p class="file" href="/">.portfolio</p>
        <p class="file" href="/">.contact</p>
        <p><a target="_blank" tabindex="-1" href="https://github.com/Yukics">Github</a></p>
        <p><a target="_blank" tabindex="-1" href="https://es.linkedin.com/in/alejo-morell-bethencourt-95966419b">Linkedin</a></p>
        <p><a target="_blank" tabindex="-1" href="https://yukics.wordpress.com/">Wordpress</a></p>
        <p><a target="_blank" tabindex="-1" href="https://twitter.com/yuki_cs">Twitter</a></p>
        <p><a target="_blank" tabindex="-1" href="https://steamcommunity.com/id/yukics">Steam</a></p>
    </div>
</div>

<style>
    .main{
        display: flex;
        flex-direction: row; 
        flex-wrap: wrap;
        align-items: flex-start;
        align-content: flex-start;
        font-size: 1.5em;
        min-width: 320px;
        min-height: fit-content;
    }
    .file{
        color:rgb(151, 211, 211);
    }
    a, p{
        word-break:break-all;
        max-height: fit-content;
        width: 200px;
        margin-top: 2vh;
        text-align: left;    
        font-weight: 500;    
        color: #646cff;
        text-decoration: inherit;
    }
    a:hover {
        color: #535bf2;
    }
</style>