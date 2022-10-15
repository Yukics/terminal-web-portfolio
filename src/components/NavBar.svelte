<script lang="ts">
    export let index:string;
</script>

<nav>
    {`web-page@yuki${index}> ls`}
</nav>

<style>
    nav{
        display: flex;
        align-items:flex-start;
        width: 100%;
        font-size: 1.5em;
    }
</style>
