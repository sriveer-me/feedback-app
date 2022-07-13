<script>
    import Card from './Card.svelte';
    import RatingBox from './RatingBox.svelte';
</script>

<div class="wrapper">
    <Card class="card--full-width">
        <form class="feedback-form__form" action="submit">
            <h1 class="feedback-form__heading-primary">How would you rate your service with us?</h1>
            <RatingBox />
        </form>
    </Card>
</div>

<style lang="scss">
    .wrapper{
        margin: 8rem 0;
    }

    .feedback-form{
        &__heading-primary{
            font-size: 2.8rem;
            text-transform: capitalize;
        }
    }
</style>