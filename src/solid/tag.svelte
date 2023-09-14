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
<path fill-rule="evenodd" clip-rule="evenodd" d="M5.25 2.25C3.59315 2.25 2.25 3.59315 2.25 5.25V9.56802C2.25 10.3637 2.56607 11.1267 3.12868 11.6893L12.7098 21.2705C13.6291 22.1898 15.0989 22.4564 16.2573 21.698C18.4242 20.2793 20.2793 18.4242 21.698 16.2573C22.4564 15.0989 22.1898 13.6291 21.2705 12.7098L11.6893 3.12868C11.1267 2.56607 10.3637 2.25 9.56802 2.25H5.25ZM6.375 7.5C6.99632 7.5 7.5 6.99632 7.5 6.375C7.5 5.75368 6.99632 5.25 6.375 5.25C5.75368 5.25 5.25 5.75368 5.25 6.375C5.25 6.99632 5.75368 7.5 6.375 7.5Z" {fill} />
</svg>
