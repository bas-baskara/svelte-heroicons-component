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
<path d="M15.3622 5.21385C18.2427 6.50093 20.25 9.391 20.25 12.7499C20.25 17.3062 16.5563 20.9999 12 20.9999C7.44365 20.9999 3.75 17.3062 3.75 12.7499C3.75 10.5378 4.62058 8.52914 6.03781 7.0477C6.8043 8.11811 7.82048 8.99755 9.00121 9.60089C9.04632 6.82521 10.348 4.35503 12.3621 2.73438C13.1255 3.75813 14.1379 4.61845 15.3622 5.21385Z" stroke="currentColor" stroke-width={strokeWidth} stroke-linecap="round" stroke-linejoin="round"/>
<path d="M12 18.0003C14.0711 18.0003 15.75 16.3214 15.75 14.2503C15.75 12.347 14.3321 10.7749 12.4949 10.5327C11.4866 11.4372 10.7862 12.6781 10.5703 14.0789C9.78769 13.8876 9.06529 13.5428 8.43682 13.0782C8.31559 13.4469 8.25 13.841 8.25 14.2503C8.25 16.3214 9.92893 18.0003 12 18.0003Z" stroke="currentColor" stroke-width={strokeWidth} stroke-linecap="round" stroke-linejoin="round"/>
</svg>
