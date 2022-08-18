<script>
    export let href, color = 'white';
</script>

<a {href} style={`--color: ${color};`}>
    <slot />
</a>

<style>
    a {
        width: 26px;
        height: 26px;
        color: var(--color);
        display: inline-block;
        transition: color 0.1s;
    }
    a:hover {
        filter: brightness(85%);
    }
    a svg {
        width: inherit;
        height: inherit;
    }
</style>