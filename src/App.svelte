<script>
	import Button from './lib/Button.svelte';
	import IconButton from './lib/IconButton.svelte';
  import FaSteam from 'svelte-icons/fa/FaSteam.svelte';
  import FaDiscord from 'svelte-icons/fa/FaDiscord.svelte';
  import FaTwitter from 'svelte-icons/fa/FaTwitter.svelte';
  import GoPlay from 'svelte-icons/go/GoPlay.svelte'

  let showVideo = false;
  console.log(showVideo);
</script>

<header>
  <img id='logo' src='/logo.png' alt='Decorporation'>
  <h2>COMING SOON</h2>
</header>


{#if showVideo}
<video autoplay muted src='/teaser.mp4' on:ended={(e) => showVideo = false}></video>
<div class='overlay' />
{:else}
<div class='play' on:click={(e) => showVideo = !showVideo}>
  <button title='Play teaser'>
    <GoPlay />
  </button>
</div>
{/if}

<main>
  <Button href='https://store.steampowered.com/app/1968950/Decorporation/' icon={FaSteam} type='primary'>
    WISHLIST NOW
  </Button>
  <div style='margin: 35px 0 15px 0'>
    <IconButton href='https://twitter.com/DecorpGame'>
      <FaTwitter />
    </IconButton>
    <IconButton href='https://discord.gg/5VNucjuBpe'>
      <FaDiscord />
    </IconButton>
  </div>
  <a href='https://cubepotato.eu'>MADE BY CUBEPOTATO.EU</a>
</main>

<footer>
</footer>

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

  video {
    width: 100vw;
    height: 100vh;
    object-fit: cover;
  }

  .overlay {
    width: 100vw;
    height: 100vh;
    position: fixed;
    top: 0; left: 0;
    background: rgba(0, 0, 0, 0.3);
    z-index: 1;
  }

  header {
    position: fixed;
    top: 80px;
    left: 0;
    right: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    z-index: 10;
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
    padding: 20px;
    text-align: center;
    z-index: 10;
  }
  main a {
    font-size: 15px;
    color: #ddd;
    font-weight: bold;
  }

  .play {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
  }

  .play button {
    background: transparent;
    border: none;
    color: #ccc;
    width: 50px;
    height: 50px;
    transition: color 0.1s;
  }

  .play button:hover {
    color: #bbb;
  }
</style>