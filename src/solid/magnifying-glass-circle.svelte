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
<path d="M8.25 10.875C8.25 9.42525 9.42525 8.25 10.875 8.25C12.3247 8.25 13.5 9.42525 13.5 10.875C13.5 11.6001 13.207 12.2553 12.7312 12.7312C12.2553 13.207 11.6001 13.5 10.875 13.5C9.42525 13.5 8.25 12.3247 8.25 10.875Z" {fill} />
<path fill-rule="evenodd" clip-rule="evenodd" d="M12 2.25C6.61522 2.25 2.25 6.61522 2.25 12C2.25 17.3848 6.61522 21.75 12 21.75C17.3848 21.75 21.75 17.3848 21.75 12C21.75 6.61522 17.3848 2.25 12 2.25ZM10.875 6.75C8.59683 6.75 6.75 8.59683 6.75 10.875C6.75 13.1532 8.59683 15 10.875 15C11.7428 15 12.5487 14.7315 13.2131 14.2737L15.2197 16.2803C15.5126 16.5732 15.9874 16.5732 16.2803 16.2803C16.5732 15.9874 16.5732 15.5126 16.2803 15.2197L14.2737 13.2131C14.7315 12.5487 15 11.7428 15 10.875C15 8.59683 13.1532 6.75 10.875 6.75Z" {fill} />
</svg>
