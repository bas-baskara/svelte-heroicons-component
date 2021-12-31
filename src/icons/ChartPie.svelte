<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher()

    export let className = "", size = "1.5", strokeWidth = "2", fill = "none"

    if (className.includes('stroke-')) strokeWidth = null

</script>

<svg xmlns="http://www.w3.org/2000/svg" class={className} {fill} viewBox="0 0 24 24" stroke="currentColor" style="width:{size}rem;height:{size}rem" on:click={() => dispatch('click')}>
    <path stroke-linecap="round" stroke-linejoin="round" stroke-width={strokeWidth} d="M11 3.055A9.001 9.001 0 1020.945 13H11V3.055z" />
    <path stroke-linecap="round" stroke-linejoin="round" stroke-width={strokeWidth} d="M20.488 9H15V3.512A9.025 9.025 0 0120.488 9z" />
</svg>