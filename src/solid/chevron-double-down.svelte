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
<path fill-rule="evenodd" clip-rule="evenodd" d="M20.0303 4.71967C20.3232 5.01256 20.3232 5.48744 20.0303 5.78033L12.5303 13.2803C12.2374 13.5732 11.7626 13.5732 11.4697 13.2803L3.96967 5.78033C3.67678 5.48744 3.67678 5.01256 3.96967 4.71967C4.26256 4.42678 4.73744 4.42678 5.03033 4.71967L12 11.6893L18.9697 4.71967C19.2626 4.42678 19.7374 4.42678 20.0303 4.71967ZM20.0303 10.7197C20.3232 11.0126 20.3232 11.4874 20.0303 11.7803L12.5303 19.2803C12.2374 19.5732 11.7626 19.5732 11.4697 19.2803L3.96967 11.7803C3.67678 11.4874 3.67678 11.0126 3.96967 10.7197C4.26256 10.4268 4.73744 10.4268 5.03033 10.7197L12 17.6893L18.9697 10.7197C19.2626 10.4268 19.7374 10.4268 20.0303 10.7197Z" {fill} />
</svg>
