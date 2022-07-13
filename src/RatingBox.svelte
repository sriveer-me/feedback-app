<script>
    import {createEventDispatcher} from 'svelte';
    let dispatcher = createEventDispatcher();

    let checkedValue = 10;
    let checkBoxes = [];

    function handleRatingChange(e){
        dispatcher('chng:rating',checkedValue);
    }

    export function setRating(rating){
        if(rating > 10)
        {
            console.log(`the rating value ${rating} is not between 1 and 10 (both inclusive)`);
            return;
        }

        checkedValue = rating;
        checkBoxes.forEach(function(box,i){
            box.checked = (checkedValue === i + 1 );
        });
    }
</script>


<div class="rate-box">
    {#each Array(10) as _, i}
        <div class="rate-box__group">
            <input type="radio" class="rate-box__input" id={`${i+1}-star-checkbox`} value={i+1} on:change={handleRatingChange} name="rate-box" checked={checkedValue === i+1} bind:this={checkBoxes[i]} >
            <label class="rate-box__label" for={`${i+1}-star-checkbox`}>{i+1}</label>
        </div>
    {/each}
</div>

<style lang="scss">
    @import './scss/variables';

    .rate-box{
        display: flex;
        justify-content: space-around;

        &__input{
            visibility: hidden;
            display: none;
        }

        &__label{
            transition: all 0.2s;
            display: inline-block;

            color: $color-dark-2;
            font-size: 1.8rem;
            font-weight: 600;
            padding: 3rem;
            max-width: 4rem;
            max-height: 4rem;

            display: flex;
            justify-content: center;
            align-items: center;

            background-color: $color-light-2;
            border-radius: 50%;
            
            cursor: pointer;
        }

        &__input:checked ~ &__label,
        &__label:hover{
            color: $color-light-2;
            background-color: $color-primary;
        }
    }
</style>