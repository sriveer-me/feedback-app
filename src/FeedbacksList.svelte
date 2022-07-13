<script>
    import FeedbackEntry from './FeedbackEntry.svelte';
    import { scale, fade } from 'svelte/transition';

    export let feedbacks;
</script>

<div class="list">
    {#each feedbacks as feedback (feedback.id)}
        <div in:scale out:fade style="width: 100%">
            <FeedbackEntry {feedback} on:del:entry />
        </div>
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