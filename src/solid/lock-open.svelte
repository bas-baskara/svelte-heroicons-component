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

<svg viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg"  style="width:{size}{hasUnit ? '':'rem'};height:{size}{hasUnit ? '':'rem'}" on:click={() => dispatch('click')} >
<path d="M18 1.5C20.8995 1.5 23.25 3.85051 23.25 6.75V10.5C23.25 10.9142 22.9142 11.25 22.5 11.25C22.0858 11.25 21.75 10.9142 21.75 10.5V6.75C21.75 4.67893 20.0711 3 18 3C15.9289 3 14.25 4.67893 14.25 6.75V9.75C15.9069 9.75 17.25 11.0931 17.25 12.75V19.5C17.25 21.1569 15.9069 22.5 14.25 22.5H3.75C2.09315 22.5 0.75 21.1569 0.75 19.5V12.75C0.75 11.0931 2.09315 9.75 3.75 9.75H12.75V6.75C12.75 3.85051 15.1005 1.5 18 1.5Z" {fill} />
</svg>
