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
<path fill-rule="evenodd" clip-rule="evenodd" d="M9.40123 4.50376C10.5557 2.50265 13.4439 2.50265 14.5983 4.50376L21.9527 17.2513C23.1065 19.2513 21.6631 21.7504 19.3541 21.7504H4.64546C2.33649 21.7504 0.893061 19.2513 2.04691 17.2513L9.40123 4.50376ZM12 9.75037C12.4142 9.75037 12.75 10.0862 12.75 10.5004V14.2504C12.75 14.6646 12.4142 15.0004 12 15.0004C11.5858 15.0004 11.25 14.6646 11.25 14.2504V10.5004C11.25 10.0862 11.5858 9.75037 12 9.75037ZM12 18.0004C12.4142 18.0004 12.75 17.6646 12.75 17.2504C12.75 16.8362 12.4142 16.5004 12 16.5004C11.5858 16.5004 11.25 16.8362 11.25 17.2504C11.25 17.6646 11.5858 18.0004 12 18.0004Z" {fill} />
</svg>
