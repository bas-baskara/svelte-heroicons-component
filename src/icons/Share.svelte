<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher()

    export let className = "", size = "1.5", strokeWidth = "2", fill = "none"

</script>

<svg xmlns="http://www.w3.org/2000/svg" class={className} {fill} viewBox="0 0 24 24" stroke="currentColor" style="width:{size}rem;height:{size}rem" on:click={() => dispatch('click')}>
    <path stroke-linecap="round" stroke-linejoin="round" stroke-width={strokeWidth} d="M8.684 13.342C8.886 12.938 9 12.482 9 12c0-.482-.114-.938-.316-1.342m0 2.684a3 3 0 110-2.684m0 2.684l6.632 3.316m-6.632-6l6.632-3.316m0 0a3 3 0 105.367-2.684 3 3 0 00-5.367 2.684zm0 9.316a3 3 0 105.368 2.684 3 3 0 00-5.368-2.684z" />
</svg>