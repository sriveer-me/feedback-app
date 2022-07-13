<script>
    import { v4 as uuidv4 } from 'uuid';
    import {createEventDispatcher} from 'svelte';

    import Card from './Card.svelte';
    import Button from './Button.svelte';
    import RatingBox from './RatingBox.svelte';

    let dispatcher = createEventDispatcher();
    let feedbackText = '';
    let ratingBox;
    let rating = 10;

    function handleRatingChange({detail}){
        rating = detail;
    }

    function handleButtonClick(){
        if(feedbackText.length <= 10)
        {
            console.log('the send button should not be active when there are less than 10 characters inside the input box.');
            return;
        }

        let feedback = {
            id: uuidv4(),
            rating: rating,
            text: feedbackText
        };

        dispatcher('new:feedback',feedback);
        
        feedbackText = '';
        ratingBox.setRating(10);
    }
</script>

<Card class="card--full-width">
    <form class="feedback-form__form" action="submit">
        <h1 class="feedback-form__heading-primary">How would you rate your service with us?</h1>
        <div class="feedback-form__input-section">
            <div class="u-margin-y-big u-width-95 u-center-x">
                <RatingBox bind:this={ratingBox} on:chng:rating={handleRatingChange}/>
            </div>
            <div class="feedback-form__input-group">
                <input class="feedback-form__input" type="text" bind:value={feedbackText}>
                <div class="u-margin-x-small">
                    <Button text="Send" disabled={feedbackText.length <= 10} on:btn:click={handleButtonClick}/>
                </div>
            </div>
            {#if feedbackText.length <= 10}
                <h2 class="feedback-form__error-heading">Text must be atleast 10 characters long</h2>
            {/if}
        </div>
    </form>
</Card>

<style lang="scss">
    @import './scss/variables';
    @import './scss/utilities';
    

    .feedback-form{
        &__heading-primary{
            font-size: 2.8rem;
            font-weight: 600;
            width: 26ch;
            margin: 0 auto;
        }

        &__input-section{
            margin-top: 4rem;
        }

        &__input-group{
            position: relative;
            display: flex;
            align-items: center;

            border-radius: 5px;
            border: 1px solid $color-dark-1;
        }

        &__input{
            flex: 1 1 100%;
            font-size: 1.8rem;
            padding: 1.4rem 1rem;

            border-radius: 5px;
            border: 0px solid transparent;

            &:focus{
                outline: 0px solid transparent;
            }
        }

        &__error-heading{
            padding-top: 10px;
            text-align: center;
            color: rebeccapurple;
            font-weight: 400;
        }
    }
</style>