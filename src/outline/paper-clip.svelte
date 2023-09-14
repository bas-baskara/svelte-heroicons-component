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
<path d="M18.375 12.739L10.682 20.432C8.92462 22.1893 6.07538 22.1893 4.31802 20.432C2.56066 18.6746 2.56066 15.8254 4.31802 14.068L15.2573 3.12868C16.4289 1.95711 18.3283 1.95711 19.4999 3.12868C20.6715 4.30025 20.6715 6.19975 19.4999 7.37132L8.55158 18.3197M8.56066 18.3107C8.55764 18.3137 8.55462 18.3167 8.55158 18.3197M14.2498 8.37865L6.43934 16.1893C5.85355 16.7751 5.85355 17.7249 6.43934 18.3107C7.02211 18.8934 7.9651 18.8964 8.55158 18.3197" stroke="currentColor" stroke-width={strokeWidth} stroke-linecap="round" stroke-linejoin="round"/>
</svg>
