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

<svg viewBox="0 0 24 24" {fill} xmlns="http://www.w3.org/2000/svg"  style="width:{size}{hasUnit ? '':'rem'};height:{size}{hasUnit ? '':'rem'}" on:click={() => dispatch('click')} >
<path d="M16.5 8.25V6C16.5 4.75736 15.4926 3.75 14.25 3.75H6C4.75736 3.75 3.75 4.75736 3.75 6V14.25C3.75 15.4926 4.75736 16.5 6 16.5H8.25M16.5 8.25H18C19.2426 8.25 20.25 9.25736 20.25 10.5V18C20.25 19.2426 19.2426 20.25 18 20.25H10.5C9.25736 20.25 8.25 19.2426 8.25 18V16.5M16.5 8.25H10.5C9.25736 8.25 8.25 9.25736 8.25 10.5V16.5" stroke="currentColor" stroke-width={strokeWidth} stroke-linecap="round" stroke-linejoin="round"/>
</svg>
