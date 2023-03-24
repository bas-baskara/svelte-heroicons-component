<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher()

    export let className = "", size = "1.5", strokeWidth = "2", fill = "none"
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

<svg viewBox="0 0 24 24" {fill} class={className} xmlns="http://www.w3.org/2000/svg"  style="width:{size}{hasUnit ? '':'rem'};height:{size}{hasUnit ? '':'rem'}"  on:keyup on:click={() => dispatch('click')} >
<path d="M10.5 21L15.75 9.75L21 21M12 18H19.5M3 5.62136C4.96557 5.37626 6.96804 5.25 9 5.25M9 5.25C10.1208 5.25 11.2326 5.28841 12.3343 5.364M9 5.25V3M12.3343 5.364C11.1763 10.6578 7.68868 15.0801 3 17.5023M12.3343 5.364C13.2298 5.42545 14.1186 5.51146 15 5.62136M10.4113 14.1162C8.78554 12.4619 7.47704 10.4949 6.58432 8.31366" stroke="currentColor" stroke-width={strokeWidth} stroke-linecap="round" stroke-linejoin="round"/>
</svg>
