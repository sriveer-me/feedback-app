<script>
    import {createEventDispatcher} from 'svelte';
    let dispatcher = createEventDispatcher();

    export let text;
    export let disabled = true;

    function handleClick(){
        dispatcher('btn:click');
    }
</script>

<button class="btn" {disabled} on:click|preventDefault={handleClick}>{text}</button>

<style lang="scss">
    button {
        color: #fff;
        border: 0;
        border-radius: 8px;
        background-color: #202142;

        width: 100px;
        height: 40px;
        cursor: pointer;
    }
    
    button:hover {
        transform: scale(0.98);
        opacity: 0.9;
    }
    button:disabled{
        background-color: #cccccc;
        color: #333;
        cursor:auto;
    }
    button:disabled:hover{
        transform:scale(1);
        opacity: 1;
    }
</style>