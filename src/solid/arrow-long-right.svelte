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
<path fill-rule="evenodd" clip-rule="evenodd" d="M16.7197 7.71967C17.0126 7.42678 17.4874 7.42678 17.7803 7.71967L21.5303 11.4697C21.8232 11.7626 21.8232 12.2374 21.5303 12.5303L17.7803 16.2803C17.4874 16.5732 17.0126 16.5732 16.7197 16.2803C16.4268 15.9874 16.4268 15.5126 16.7197 15.2197L19.1893 12.75H3C2.58579 12.75 2.25 12.4142 2.25 12C2.25 11.5858 2.58579 11.25 3 11.25H19.1893L16.7197 8.78033C16.4268 8.48744 16.4268 8.01256 16.7197 7.71967Z" {fill} />
</svg>
