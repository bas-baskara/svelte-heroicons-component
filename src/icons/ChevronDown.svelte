<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher()

    export let className = "", size = "1.5", strokeWidth = "2", fill = "none"

</script>

<svg xmlns="http://www.w3.org/2000/svg" class={className} {fill} viewBox="0 0 24 24" stroke="currentColor" style="width:{size};height:{size}" on:click={() => dispatch('click')}>
    <path stroke-linecap="round" stroke-linejoin="round" stroke-width={strokeWidth} d="M19 13l-7 7-7-7m14-8l-7 7-7-7" />
</svg>