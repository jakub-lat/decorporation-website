<script>
    export let href, icon, type = 'secondary';
    const colors = {
        primary: ['#d6173c', 'white', '#8a0e26'], 
        secondary: ['#ccc', 'black', '#444'],
    }
</script>

<a {href} style={`--bg-color: ${colors[type][0]}; --text-color: ${colors[type][1]}; --border-color: ${colors[type][2]}`}>
    {#if icon}
    <div class='icon'>
        <svelte:component this={icon} class='icon' />
    </div>
    {/if}
    <slot />
</a>

<style>
    a {
        color: var(--text-color);
        background-color: var(--bg-color);
        padding: 10px 20px;
        text-decoration: none;
        font-weight: bold;
        font-size: 18px;
        margin: 10px;
        border: 2px solid var(--border-color);
        border-radius: 5px;
        transition: all 0.2s;
        display: inline-flex;
        justify-content: center;
    }
    a .icon {
        width: 22px;
        height: 22px;
        margin-right: 10px;
    }
    a:hover {
        filter: brightness(85%);
    }
</style>
