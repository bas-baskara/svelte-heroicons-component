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
<path d="M15.75 5.25C17.4069 5.25 18.75 6.59315 18.75 8.25M21.75 8.25C21.75 11.5637 19.0637 14.25 15.75 14.25C15.3993 14.25 15.0555 14.2199 14.7213 14.1622C14.1583 14.0649 13.562 14.188 13.158 14.592L10.5 17.25H8.25V19.5H6V21.75H2.25V18.932C2.25 18.3352 2.48705 17.7629 2.90901 17.341L9.408 10.842C9.81202 10.438 9.93512 9.84172 9.83785 9.2787C9.7801 8.94446 9.75 8.60074 9.75 8.25C9.75 4.93629 12.4363 2.25 15.75 2.25C19.0637 2.25 21.75 4.93629 21.75 8.25Z" stroke="currentColor" stroke-width={strokeWidth} stroke-linecap="round" stroke-linejoin="round"/>
</svg>
