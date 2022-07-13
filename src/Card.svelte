<script>
    let clazz;
    export {clazz as class};
</script>

<div class={`card ${clazz}`}>
    <slot></slot>
</div>

<style lang="scss">
    @import './scss/variables';

    .card{
        display: inline-block;
        position: relative;

        max-width: 90rem;
        padding: 3rem 8rem;
        background-color: $color-light-1;
        border-radius: .5rem;

        &--full-width{
            width: 100%;
        }
    }
</style>