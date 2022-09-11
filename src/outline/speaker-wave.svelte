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

<svg viewBox="0 0 24 24" {fill} class={className} xmlns="http://www.w3.org/2000/svg"  style="width:{size}{hasUnit ? '':'rem'};height:{size}{hasUnit ? '':'rem'}" on:click={() => dispatch('click')} >
<path d="M19.114 5.63591C22.6287 9.15063 22.6287 14.8491 19.114 18.3638M16.4626 8.28765C18.5129 10.3379 18.5129 13.662 16.4626 15.7123M6.75 8.24993L11.4697 3.53026C11.9421 3.05778 12.75 3.39241 12.75 4.06059V19.9393C12.75 20.6074 11.9421 20.9421 11.4697 20.4696L6.75 15.7499H4.50905C3.62971 15.7499 2.8059 15.2435 2.57237 14.3957C2.36224 13.6329 2.25 12.8295 2.25 11.9999C2.25 11.1703 2.36224 10.367 2.57237 9.60416C2.8059 8.7564 3.62971 8.24993 4.50905 8.24993H6.75Z" stroke="currentColor" stroke-width={strokeWidth} stroke-linecap="round" stroke-linejoin="round"/>
</svg>
