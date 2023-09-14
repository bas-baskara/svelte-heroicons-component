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
<path fill-rule="evenodd" clip-rule="evenodd" d="M12 2.25C12.4142 2.25 12.75 2.58579 12.75 3L12.75 19.1893L15.2197 16.7197C15.5126 16.4268 15.9874 16.4268 16.2803 16.7197C16.5732 17.0126 16.5732 17.4874 16.2803 17.7803L12.5303 21.5303C12.2374 21.8232 11.7626 21.8232 11.4697 21.5303L7.71967 17.7803C7.42678 17.4874 7.42678 17.0126 7.71967 16.7197C8.01256 16.4268 8.48744 16.4268 8.78033 16.7197L11.25 19.1893L11.25 3C11.25 2.58579 11.5858 2.25 12 2.25Z" {fill} />
</svg>
