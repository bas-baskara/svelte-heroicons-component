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
<path d="M3 8.68819C3 7.82439 3.93317 7.28285 4.68316 7.71141L11.7906 11.7728C12.5464 12.2047 12.5464 13.2945 11.7906 13.7264L4.68316 17.7878C3.93317 18.2164 3 17.6748 3 16.811V8.68819Z" stroke="currentColor" stroke-width={strokeWidth} stroke-linecap="round" stroke-linejoin="round"/>
<path d="M12.75 8.68819C12.75 7.82439 13.6832 7.28285 14.4332 7.71141L21.5406 11.7728C22.2964 12.2047 22.2964 13.2945 21.5406 13.7264L14.4332 17.7878C13.6832 18.2164 12.75 17.6748 12.75 16.811V8.68819Z" stroke="currentColor" stroke-width={strokeWidth} stroke-linecap="round" stroke-linejoin="round"/>
</svg>
