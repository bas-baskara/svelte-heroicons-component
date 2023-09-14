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
<path d="M3.47804 2.40479C3.2133 2.32789 2.92771 2.40242 2.73432 2.59889C2.54093 2.79536 2.47091 3.08209 2.55198 3.34558L4.98426 11.2505H13.5C13.9142 11.2505 14.25 11.5863 14.25 12.0005C14.25 12.4147 13.9142 12.7505 13.5 12.7505H4.98427L2.55207 20.6551C2.471 20.9186 2.54102 21.2054 2.73441 21.4018C2.92781 21.5983 3.2134 21.6728 3.47814 21.5959C10.1767 19.6499 16.3974 16.5819 21.9233 12.6092C22.1193 12.4683 22.2355 12.2416 22.2355 12.0002C22.2355 11.7588 22.1193 11.5322 21.9233 11.3913C16.3974 7.41866 10.1767 4.3507 3.47804 2.40479Z" {fill} />
</svg>
