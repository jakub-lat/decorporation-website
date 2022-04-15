<script>
	import Button from './lib/Button.svelte';
</script>

<header>
  <img id='logo' src='/logo.png' alt='Decorporation'>
  <h2>COMING SOON</h2>
</header>

<main>
  <Button href='https://store.steampowered.com/app/1968950/Decorporation/' icon='steam'>
    STEAM
  </Button>
  <Button href='https://twitter.com/DecorpGame' icon='twitter'>
    TWITTER
  </Button>
  <Button href='https://discord.gg/j5E7D3yjkQ' icon='discord'>
    DISCORD
  </Button>
  <br />
  <br />
  <a href='https://cubepotato.eu'>MADE BY CUBEPOTATO.EU</a>
</main>

<style>
  :global(*) {
    box-sizing: border-box;
    font-family: monospace;
  }

  :global(body) {
    padding: 0;
    margin: 0;
    width: 100vw;
    height: 100vh;
    background: url('/bg.png');
    background-size: cover;
    background-position: center;
  }

  :global(#app) {
    display: flex;
    height: 100vh;
  }

  header {
    position: fixed;
    top: 80px;
    left: 0;
    right: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  header h2 {
    font-size: 25px;
    color: #ddd;
  }

  #logo {
    width: min(700px, 90%);
  }

  main {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    padding: 40px;
    text-align: center;
  }
  a {
    font-size: 17px;
    color: #eee;
    font-weight: bold;
  }
</style>