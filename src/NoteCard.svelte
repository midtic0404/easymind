<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
    export let description;
</script>

<style>
</style>

<div class="column is-4 is-offset-1">
    <div class="card">
        <div class="card-content">
            <p class="title">
                {description}
            </p>
        </div>
        <footer class="card-footer">
            <button class="card-footer-item button is-danger is-light"
                on:click={() => {dispatch('delete')}}>Delete</button>
        </footer>
    </div>
</div>