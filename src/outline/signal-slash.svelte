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
<path d="M3 3L11.7348 11.7348M11.7348 11.7348C11.8027 11.667 11.8964 11.625 12 11.625C12.2071 11.625 12.375 11.7929 12.375 12C12.375 12.1036 12.333 12.1973 12.2652 12.2652M11.7348 11.7348L12.2652 12.2652M12.2652 12.2652L21 21M14.6517 9.34835C16.1161 10.8128 16.1161 13.1872 14.6517 14.6516M16.773 7.22703C19.409 9.86307 19.409 14.1369 16.773 16.773M18.8943 5.10571C22.7019 8.91332 22.7019 15.0867 18.8943 18.8943M9.34835 14.6516C8.75129 14.0546 8.39765 13.3063 8.28743 12.5301M7.22703 16.773C5.35299 14.8989 4.81126 12.1971 5.60184 9.84448M5.10571 18.8943C2.03824 15.8268 1.44197 11.2239 3.3169 7.55955M12 12H12.0075V12.0075H12V12Z" stroke="currentColor" stroke-width={strokeWidth} stroke-linecap="round" stroke-linejoin="round"/>
</svg>
