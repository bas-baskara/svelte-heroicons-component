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

<svg viewBox="0 0 24 24" {fill} class={className} xmlns="http://www.w3.org/2000/svg"  style="width:{size}{hasUnit ? '':'rem'};height:{size}{hasUnit ? '':'rem'}"  on:keyup role="button" tabindex="0" on:click={() => dispatch('click')} >
<path d="M21 16.811C21 17.6748 20.0668 18.2164 19.3168 17.7878L12.2094 13.7264C11.4536 13.2945 11.4536 12.2047 12.2094 11.7728L19.3168 7.71141C20.0668 7.28285 21 7.82439 21 8.68819V16.811Z" stroke="currentColor" stroke-width={strokeWidth} stroke-linecap="round" stroke-linejoin="round"/>
<path d="M11.25 16.811C11.25 17.6748 10.3168 18.2164 9.56684 17.7878L2.45935 13.7264C1.70356 13.2945 1.70356 12.2047 2.45935 11.7728L9.56684 7.71141C10.3168 7.28285 11.25 7.82439 11.25 8.68819L11.25 16.811Z" stroke="currentColor" stroke-width={strokeWidth} stroke-linecap="round" stroke-linejoin="round"/>
</svg>
