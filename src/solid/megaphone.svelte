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
<path d="M16.8812 4.34562C14.81 5.17419 12.5917 5.71339 10.276 5.9132C9.60847 5.97079 8.93276 6.0002 8.25 6.0002H7.5C4.60051 6.0002 2.25 8.35071 2.25 11.2502C2.25 13.8498 4.13945 16.0081 6.61997 16.4268C6.95424 17.7958 7.41805 19.114 7.99764 20.3676C8.46171 21.3714 9.67181 21.6876 10.5803 21.1631L11.2366 20.7842C12.1167 20.2761 12.4023 19.1915 12.0087 18.3161C11.7738 17.7937 11.5642 17.2576 11.3814 16.7092C13.2988 16.9672 15.1419 17.459 16.8812 18.1548C17.6069 15.9854 18 13.6637 18 11.2502C18 8.83666 17.6069 6.51496 16.8812 4.34562Z" {fill} />
<path d="M18.2606 3.7409C19.0641 6.0966 19.5 8.62249 19.5 11.2502C19.5 13.8779 19.0641 16.4038 18.2606 18.7595V18.7595C18.2054 18.9212 18.1487 19.0823 18.0901 19.2424C17.9477 19.6314 18.1476 20.0621 18.5366 20.2045C18.9256 20.3469 19.3563 20.147 19.4987 19.758C19.6387 19.3755 19.7696 18.9886 19.891 18.5975C20.4147 16.9107 20.7627 15.147 20.914 13.328C21.431 12.7895 21.75 12.0569 21.75 11.2502C21.75 10.4436 21.431 9.71091 20.914 9.17246C20.7627 7.35338 20.4147 5.58966 19.891 3.90292C19.7696 3.51183 19.6387 3.1249 19.4987 2.7424C19.3563 2.35342 18.9256 2.15352 18.5366 2.29591C18.1476 2.43829 17.9477 2.86904 18.0901 3.25801C18.1487 3.41813 18.2055 3.57916 18.2606 3.7409V3.7409Z" {fill} />
</svg>
