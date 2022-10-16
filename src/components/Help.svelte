<script lang="ts">
</script>

<div>
    <div class="main">
        <div>
            <h4>You might entered a wrong command, there is hint:</h4>
        </div>

        <ul>
            <li>cls -> Wipes the commands history</li>
            <li>ls -> Show related links</li>
            <li>cv -> Prints info about the author</li>
            <li>help -> Prints this output</li>
        </ul>

    </div>
</div>

<style>
    .main{
        display: flex;
        flex-direction: column; 
        flex-wrap: wrap;
        align-items: flex-start;
        align-content: flex-start;
        font-size: 1.5em;
        /* min-height: fit-content; */
    }
    h4{
        color: rgb(161, 161, 161);
    }
    ul{
        width: 100%;
    }
    li{
        padding: 2%;
        color: rgb(161, 161, 161);
    }
</style>