<script>
    import { createEventDispatcher } from 'svelte';
    import Card from './Card.svelte';

    export let feedback;

    let dispatcher = createEventDispatcher();

    function handleClose(){
        dispatcher('del:entry',feedback.id);
    }
</script>

<Card class="card--full-width">
    <div class="entry__rating">{feedback.rating}</div>
    <h1 class="entry__text">{feedback.text}</h1>
    <h1 class="entry__close" on:click={handleClose}>x</h1>
</Card>

<style lang="scss">
    @import './scss/variables';

    .entry{
        &__rating{
            position: absolute;
            top: -10px;
            left: -10px;

            font-size: 1.8rem;
            font-weight: 600;
            color: $color-light-1;
            background-color: $color-primary;
            border-radius: 50%;
            border: 1px solid #eee;
            
            width: 5rem;
            height: 5rem;
            padding: 1rem;
            text-align: center;
        }

        &__close{
            font-weight: 600;
            position: absolute;
            top: .5rem;
            right: 2rem;

            cursor: pointer;
        }

        &__text{
            margin-top: 1rem;
            font-weight: 400;
            font-size: 1.8rem;
        }
    }
</style>