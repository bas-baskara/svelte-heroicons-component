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
<path d="M19.5 22.5002C21.1569 22.5002 22.5 21.1571 22.5 19.5002V11.3264L15.6212 15.3483L19.1056 17.2245C19.4703 17.4209 19.6067 17.8757 19.4104 18.2404C19.214 18.6051 18.7591 18.7416 18.3944 18.5452L12.7112 15.485C12.2672 15.2459 11.7328 15.2459 11.2889 15.485L5.60558 18.5452C5.24087 18.7416 4.78603 18.6051 4.58965 18.2404C4.39327 17.8757 4.52972 17.4209 4.89442 17.2245L8.37878 15.3483L1.5 11.3264V19.5002C1.5 21.1571 2.84315 22.5002 4.5 22.5002L19.5 22.5002Z" {fill} />
<path d="M1.5 9.58886V8.84412C1.5 7.74048 2.10597 6.72595 3.0777 6.20271L10.5777 2.16425C11.4656 1.68614 12.5344 1.68614 13.4223 2.16425L20.9223 6.20271C21.894 6.72595 22.5 7.74048 22.5 8.84413V9.58886L14.0742 14.5153L13.4223 14.1643C12.5344 13.6862 11.4656 13.6862 10.5777 14.1643L9.92585 14.5153L1.5 9.58886Z" {fill} />
</svg>
