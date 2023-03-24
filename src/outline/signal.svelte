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

<svg viewBox="0 0 24 24" {fill} class={className} xmlns="http://www.w3.org/2000/svg"  style="width:{size}{hasUnit ? '':'rem'};height:{size}{hasUnit ? '':'rem'}"  on:keyup on:click={() => dispatch('click')} >
<path d="M9.34835 14.6514C7.88388 13.1869 7.88388 10.8126 9.34835 9.34811M14.6517 9.34811C16.1161 10.8126 16.1161 13.1869 14.6517 14.6514M7.22703 16.7727C4.59099 14.1367 4.59099 9.86283 7.22703 7.22679M16.773 7.22679C19.409 9.86283 19.409 14.1367 16.773 16.7727M5.10571 18.8941C1.2981 15.0864 1.2981 8.91308 5.10571 5.10547M18.8943 5.10547C22.7019 8.91308 22.7019 15.0864 18.8943 18.8941M12 11.9998H12.0075V12.0073H12V11.9998ZM12.375 11.9998C12.375 12.2069 12.2071 12.3748 12 12.3748C11.7929 12.3748 11.625 12.2069 11.625 11.9998C11.625 11.7927 11.7929 11.6248 12 11.6248C12.2071 11.6248 12.375 11.7927 12.375 11.9998Z" stroke="currentColor" stroke-width={strokeWidth} stroke-linecap="round" stroke-linejoin="round"/>
</svg>
