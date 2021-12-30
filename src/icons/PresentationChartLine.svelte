<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher()

    export let className = "", size = "1.5", strokeWidth = "2", fill = "none"

</script>

<svg xmlns="http://www.w3.org/2000/svg" class={className} {fill} viewBox="0 0 24 24" stroke="currentColor" style="width:{size}rem;height:{size}rem" on:click={() => dispatch('click')}>
    <path stroke-linecap="round" stroke-linejoin="round" stroke-width={strokeWidth} d="M7 12l3-3 3 3 4-4M8 21l4-4 4 4M3 4h18M4 4h16v12a1 1 0 01-1 1H5a1 1 0 01-1-1V4z" />
</svg>