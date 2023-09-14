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
<path d="M21 7.5L21 18M15 7.5V18M3 16.8114V8.68858C3 7.82478 3.93317 7.28324 4.68316 7.7118L11.7906 11.7732C12.5464 12.2051 12.5464 13.2949 11.7906 13.7268L4.68316 17.7882C3.93317 18.2168 3 17.6752 3 16.8114Z" stroke="currentColor" stroke-width={strokeWidth} stroke-linecap="round" stroke-linejoin="round"/>
</svg>
