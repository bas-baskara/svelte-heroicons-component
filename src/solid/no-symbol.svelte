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
<path fill-rule="evenodd" clip-rule="evenodd" d="M6.72048 5.65982L18.3402 17.2795C21.0455 14.0383 20.8767 9.20943 17.8336 6.16637C14.7906 3.12331 9.96171 2.95446 6.72048 5.65982ZM17.2795 18.3402L5.65982 6.72048C2.95446 9.96171 3.12331 14.7906 6.16637 17.8336C9.20943 20.8767 14.0383 21.0455 17.2795 18.3402ZM5.10571 5.10571C8.91332 1.2981 15.0867 1.2981 18.8943 5.10571C22.7019 8.91332 22.7019 15.0867 18.8943 18.8943C15.0867 22.7019 8.91332 22.7019 5.10571 18.8943C1.2981 15.0867 1.2981 8.91332 5.10571 5.10571Z" {fill} />
</svg>
