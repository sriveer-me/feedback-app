<script>
    import Card from './Card.svelte';
    import Button from './Button.svelte';
    import RatingBox from './RatingBox.svelte';

    let feedbackText = '';
</script>

<div class="wrapper">
    <Card class="card--full-width">
        <form class="feedback-form__form" action="submit">
            <h1 class="feedback-form__heading-primary">How would you rate your service with us?</h1>
            <div class="feedback-form__input-section">
                <div class="u-margin-y-big u-width-95 u-center-x">
                    <RatingBox />
                </div>
                <div class="feedback-form__input-group">
                    <input class="feedback-form__input" type="text" bind:value={feedbackText}>
                    <div class="u-margin-x-small">
                        <Button text="Send" disabled={feedbackText.length <= 10} on:btn:click={ ()=>{console.log('button clicked!')}}/>
                    </div>
                </div>
                {#if feedbackText.length <= 10}
                    <h2 class="feedback-form__error-heading">Text must be atleast 10 characters long</h2>
                {/if}
            </div>
        </form>
    </Card>
</div>

<style lang="scss">
    @import './scss/variables';
    @import './scss/utilities';
    .wrapper{
        margin: 8rem 0;
    }

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