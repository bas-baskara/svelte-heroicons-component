<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher()

    export let className = "", size = "1.5", strokeWidth = "2", fill = "#0F172A"
    let units = ['cm', 'mm', 'in', 'px', 'pt', 'pc'], hasUnit

    $: {
        units.forEach(v => {
            if (size?.toString().indexOf(v) != -1) {
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

<svg viewBox="0 0 24 24" class={className} fill="currentColor" xmlns="http://www.w3.org/2000/svg"  style="width:{size}{hasUnit ? '':'rem'};height:{size}{hasUnit ? '':'rem'}" on:click={() => dispatch('click')} >
<path d="M21.7312 2.26884C20.706 1.24372 19.044 1.24372 18.0189 2.26884L16.8617 3.426L20.574 7.13831L21.7312 5.98116C22.7563 4.95603 22.7563 3.29397 21.7312 2.26884Z" {fill} />
<path d="M19.5134 8.19897L15.801 4.48666L3.65021 16.6375C3.03342 17.2543 2.58003 18.015 2.33101 18.851L1.53123 21.5359C1.45261 21.7998 1.52496 22.0856 1.71969 22.2803C1.91442 22.4751 2.2002 22.5474 2.46413 22.4688L5.14902 21.669C5.98499 21.42 6.74574 20.9666 7.36253 20.3498L19.5134 8.19897Z" {fill} />
</svg>
