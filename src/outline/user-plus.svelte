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
<path d="M19 7.5V10.5M19 10.5V13.5M19 10.5H22M19 10.5H16M13.75 6.375C13.75 8.23896 12.239 9.75 10.375 9.75C8.51104 9.75 7 8.23896 7 6.375C7 4.51104 8.51104 3 10.375 3C12.239 3 13.75 4.51104 13.75 6.375ZM4.00092 19.2343C4.00031 19.198 4 19.1615 4 19.125C4 15.6042 6.85418 12.75 10.375 12.75C13.8958 12.75 16.75 15.6042 16.75 19.125V19.1276C16.75 19.1632 16.7497 19.1988 16.7491 19.2343C14.8874 20.3552 12.7065 21 10.375 21C8.04353 21 5.86264 20.3552 4.00092 19.2343Z" stroke="currentColor" stroke-width={strokeWidth} stroke-linecap="round" stroke-linejoin="round"/>
</svg>
