<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher()

    export let className = "", size = "1.5"
    let units = ['cm', 'mm', 'in', 'px', 'pt', 'pc'], hasUnit

    $: {
        units.forEach(v => {
            if (size?.toString().indexOf(v) != -1) {
                hasUnit = true
                return
            }
        })
    }

    if (className) {
        const classes = className.split(' ')
        classes.forEach(val => {
            const name = val.replace(/[:(sm)(md)(lg)(xl)(2xl)]/g, '')
            if (name.slice(0,2) == 'w-') {
                size = null
                return
            }
        })
    }

</script>

<svg xmlns="http://www.w3.org/2000/svg" class={className} viewBox="0 0 20 20" fill="currentColor" style="width:{size}{hasUnit ? '':'rem'};height:{size}{hasUnit ? '':'rem'}" on:click={() => dispatch('click')}>
    <path d="M11 3a1 1 0 100 2h2.586l-6.293 6.293a1 1 0 101.414 1.414L15 6.414V9a1 1 0 102 0V4a1 1 0 00-1-1h-5z" />
    <path d="M5 5a2 2 0 00-2 2v8a2 2 0 002 2h8a2 2 0 002-2v-3a1 1 0 10-2 0v3H5V7h3a1 1 0 000-2H5z" />
</svg>