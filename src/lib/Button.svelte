<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

    export let href = '', icon, type = 'secondary';
    const colors = {
        primary: ['#d6173c', 'white', '#8a0e26'], 
        secondary: ['#ccc', 'black', '#444'],
    }

    function click() {
        dispatch('click');
    }
</script>

<svelte:element this={href ? 'a' : 'button'} class='btn' on:click={click} {href} style={`--bg-color: ${colors[type][0]}; --text-color: ${colors[type][1]}; --border-color: ${colors[type][2]}`}>
    {#if icon}
    <div class='icon'>
        <svelte:component this={icon} class='icon' />
    </div>
    {/if}
    <slot />
</svelte:element>

<style>
    .btn {
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
        cursor: pointer;
    }
    .btn .icon {
        width: 22px;
        height: 22px;
        margin-right: 10px;
    }
    .btn:hover {
        filter: brightness(85%);
    }
</style>
