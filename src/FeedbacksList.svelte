<script>
    import FeedbackEntry from './FeedbackEntry.svelte';

    export let feedbacks;
</script>

<div class="list">
    {#each feedbacks as feedback}
        <FeedbackEntry {feedback} on:del:entry />
    {/each}
</div>

<style>
    .list{
        display: flex;
        flex-direction: column;
        align-items: center;

        row-gap: 3rem;
    }
</style>