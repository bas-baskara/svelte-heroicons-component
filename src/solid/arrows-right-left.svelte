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

<svg viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg"  style="width:{size}{hasUnit ? '':'rem'};height:{size}{hasUnit ? '':'rem'}" on:click={() => dispatch('click')} >
<path fill-rule="evenodd" clip-rule="evenodd" d="M15.9697 2.46967C16.2626 2.17678 16.7374 2.17678 17.0303 2.46967L21.5303 6.96967C21.671 7.11032 21.75 7.30109 21.75 7.5C21.75 7.69891 21.671 7.88968 21.5303 8.03033L17.0303 12.5303C16.7374 12.8232 16.2626 12.8232 15.9697 12.5303C15.6768 12.2374 15.6768 11.7626 15.9697 11.4697L19.1893 8.25L7.5 8.25C7.08579 8.25 6.75 7.91421 6.75 7.5C6.75 7.08579 7.08579 6.75 7.5 6.75L19.1893 6.75L15.9697 3.53033C15.6768 3.23744 15.6768 2.76256 15.9697 2.46967ZM8.03033 11.4697C8.32322 11.7626 8.32322 12.2374 8.03033 12.5303L4.81066 15.75H16.5C16.9142 15.75 17.25 16.0858 17.25 16.5C17.25 16.9142 16.9142 17.25 16.5 17.25H4.81066L8.03033 20.4697C8.32322 20.7626 8.32322 21.2374 8.03033 21.5303C7.73744 21.8232 7.26256 21.8232 6.96967 21.5303L2.46967 17.0303C2.17678 16.7374 2.17678 16.2626 2.46967 15.9697L6.96967 11.4697C7.26256 11.1768 7.73744 11.1768 8.03033 11.4697Z" {fill} />
</svg>
