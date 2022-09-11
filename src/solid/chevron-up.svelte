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
<path fill-rule="evenodd" clip-rule="evenodd" d="M11.4697 7.71967C11.7626 7.42678 12.2374 7.42678 12.5303 7.71967L20.0303 15.2197C20.3232 15.5126 20.3232 15.9874 20.0303 16.2803C19.7374 16.5732 19.2626 16.5732 18.9697 16.2803L12 9.31066L5.03033 16.2803C4.73744 16.5732 4.26256 16.5732 3.96967 16.2803C3.67678 15.9874 3.67678 15.5126 3.96967 15.2197L11.4697 7.71967Z" {fill} />
</svg>
