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
<path fill-rule="evenodd" clip-rule="evenodd" d="M11.4843 2.1698C11.7735 1.89587 12.2265 1.89587 12.5157 2.1698C14.5325 4.07977 17.2538 5.25011 20.25 5.25011C20.2977 5.25011 20.3453 5.24981 20.3928 5.24922C20.7202 5.24515 21.0123 5.4539 21.1146 5.76491C21.5271 7.01968 21.75 8.35963 21.75 9.75015C21.75 15.6922 17.6859 20.6831 12.1869 22.0984C12.0643 22.13 11.9357 22.13 11.8131 22.0984C6.31406 20.6831 2.25 15.6922 2.25 9.75015C2.25 8.35963 2.47287 7.01968 2.88541 5.76491C2.98767 5.4539 3.27984 5.24515 3.60721 5.24922C3.65473 5.24981 3.70233 5.25011 3.75 5.25011C6.74624 5.25011 9.46752 4.07977 11.4843 2.1698ZM12 8.25009C12.4142 8.25009 12.75 8.58588 12.75 9.00009V12.7501C12.75 13.1643 12.4142 13.5001 12 13.5001C11.5858 13.5001 11.25 13.1643 11.25 12.7501V9.00009C11.25 8.58588 11.5858 8.25009 12 8.25009ZM12 15.0001C11.5858 15.0001 11.25 15.3359 11.25 15.7501V15.7576C11.25 16.1718 11.5858 16.5076 12 16.5076H12.0075C12.4217 16.5076 12.7575 16.1718 12.7575 15.7576V15.7501C12.7575 15.3359 12.4217 15.0001 12.0075 15.0001H12Z" {fill} />
</svg>
