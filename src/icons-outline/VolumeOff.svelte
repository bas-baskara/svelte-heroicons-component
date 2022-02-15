<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher()

    export let className = "", size = "1.5", strokeWidth = "2", fill = "none"
    let units = ['cm', 'mm', 'in', 'px', 'pt', 'pc'], hasUnit

    $: {
        units.forEach(v => {
            if (size.toString().indexOf(v) != -1) {
                hasUnit = true
                return
            }
        })
    }

    if (className.includes('stroke-')) strokeWidth = null

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

<svg xmlns="http://www.w3.org/2000/svg" class={className} {fill} viewBox="0 0 24 24" stroke="currentColor" style="width:{size}{hasUnit ? '':'rem'};height:{size}{hasUnit ? '':'rem'}" on:click={() => dispatch('click')}>
    <path stroke-linecap="round" stroke-linejoin="round" stroke-width={strokeWidth} d="M5.586 15H4a1 1 0 01-1-1v-4a1 1 0 011-1h1.586l4.707-4.707C10.923 3.663 12 4.109 12 5v14c0 .891-1.077 1.337-1.707.707L5.586 15z" clip-rule="evenodd" />
    <path stroke-linecap="round" stroke-linejoin="round" stroke-width={strokeWidth} d="M17 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2" />
</svg>