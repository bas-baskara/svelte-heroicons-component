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

<svg viewBox="0 0 24 24" class={className} fill="currentColor" xmlns="http://www.w3.org/2000/svg"  style="width:{size}{hasUnit ? '':'rem'};height:{size}{hasUnit ? '':'rem'}"  on:keyup role="button" tabindex="0" on:click={() => dispatch('click')} >
<path fill-rule="evenodd" clip-rule="evenodd" d="M11.4697 4.71967C11.7626 4.42678 12.2374 4.42678 12.5303 4.71967L20.0303 12.2197C20.3232 12.5126 20.3232 12.9874 20.0303 13.2803C19.7374 13.5732 19.2626 13.5732 18.9697 13.2803L12 6.31066L5.03033 13.2803C4.73744 13.5732 4.26256 13.5732 3.96967 13.2803C3.67678 12.9874 3.67678 12.5126 3.96967 12.2197L11.4697 4.71967ZM12 12.3107L5.03033 19.2803C4.73744 19.5732 4.26256 19.5732 3.96967 19.2803C3.67678 18.9874 3.67678 18.5126 3.96967 18.2197L11.4697 10.7197C11.7626 10.4268 12.2374 10.4268 12.5303 10.7197L20.0303 18.2197C20.3232 18.5126 20.3232 18.9874 20.0303 19.2803C19.7374 19.5732 19.2626 19.5732 18.9697 19.2803L12 12.3107Z" {fill} />
</svg>
