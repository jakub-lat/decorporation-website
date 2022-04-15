<script>
    export let href, icon;
</script>

<a {href}>
    {#if icon}<img src={`/icons/${icon}.svg`} alt={icon}>{/if}
    <slot />
</a>

<style>
    a {
        color: black;
        background: #ccc;
        padding: 10px 20px;
        text-decoration: none;
        font-weight: bold;
        font-size: 18px;
        margin: 10px;
        border: 2px solid #444;
        border-radius: 5px;
        transition: all 0.2s;
        display: inline-flex;
        justify-content: center;
    }
    a img {
        width: 20px;
        margin-right: 10px;
    }
    a:hover {
        background: #aaaaaa;
    }
</style>
