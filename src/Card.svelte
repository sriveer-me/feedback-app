<div class="card">
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
    }
</style>