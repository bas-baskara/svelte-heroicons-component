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

<svg viewBox="0 0 24 24" class={className} fill="currentColor" xmlns="http://www.w3.org/2000/svg"  style="width:{size}{hasUnit ? '':'rem'};height:{size}{hasUnit ? '':'rem'}"  on:keyup on:click={() => dispatch('click')} >
<path fill-rule="evenodd" clip-rule="evenodd" d="M12 1.5C9.10051 1.5 6.75 3.85051 6.75 6.75V9.75C5.09315 9.75 3.75 11.0931 3.75 12.75V19.5C3.75 21.1569 5.09315 22.5 6.75 22.5H17.25C18.9069 22.5 20.25 21.1569 20.25 19.5V12.75C20.25 11.0931 18.9069 9.75 17.25 9.75V6.75C17.25 3.85051 14.8995 1.5 12 1.5ZM15.75 9.75V6.75C15.75 4.67893 14.0711 3 12 3C9.92893 3 8.25 4.67893 8.25 6.75V9.75H15.75Z" {fill} />
</svg>
