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
<path d="M13.5 20.9999V13.4999C13.5 13.0856 13.8358 12.7499 14.25 12.7499H17.25C17.6642 12.7499 18 13.0856 18 13.4999V20.9999M13.5 20.9999H2.36088M13.5 20.9999H18M18 20.9999H21.6391M20.25 20.9999V9.34863M3.75 20.9999V9.34888M3.75 9.34888C4.89729 10.012 6.38977 9.85281 7.37132 8.87127C7.41594 8.82665 7.45886 8.78097 7.50008 8.73432C8.04979 9.35708 8.85402 9.74986 9.75 9.74986C10.646 9.74986 11.4503 9.35704 12 8.73423C12.5497 9.35704 13.354 9.74986 14.25 9.74986C15.1459 9.74986 15.9501 9.35713 16.4998 8.73443C16.541 8.78101 16.5838 8.82662 16.6284 8.87118C17.61 9.85281 19.1027 10.012 20.25 9.34863M3.75 9.34888C3.52788 9.2205 3.31871 9.06129 3.12868 8.87127C1.95711 7.69969 1.95711 5.8002 3.12868 4.62863L4.31797 3.43934C4.59927 3.15804 4.9808 3 5.37863 3H18.6212C19.019 3 19.4005 3.15804 19.6818 3.43934L20.871 4.62854C22.0426 5.80011 22.0426 7.69961 20.871 8.87118C20.6811 9.06113 20.472 9.22028 20.25 9.34863M6.75 17.9999H10.5C10.9142 17.9999 11.25 17.6641 11.25 17.2499V13.4999C11.25 13.0856 10.9142 12.7499 10.5 12.7499H6.75C6.33579 12.7499 6 13.0856 6 13.4999V17.2499C6 17.6641 6.33579 17.9999 6.75 17.9999Z" stroke="currentColor" stroke-width={strokeWidth} stroke-linecap="round" stroke-linejoin="round"/>
</svg>
