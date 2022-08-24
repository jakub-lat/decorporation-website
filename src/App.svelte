<script>
	import Button from './lib/Button.svelte';
	import IconButton from './lib/IconButton.svelte';
  import FaSteam from 'svelte-icons/fa/FaSteam.svelte';
  import FaDiscord from 'svelte-icons/fa/FaDiscord.svelte';
  import FaTwitter from 'svelte-icons/fa/FaTwitter.svelte';
  import GoPlay from 'svelte-icons/go/GoPlay.svelte'
  import IoMdClose from 'svelte-icons/io/IoMdClose.svelte'
  import YouTubePlayer from 'youtube-player';

  let showVideo = false;
  let player, video, playerState;

  $: if(video && !player) {
    // console.log(video);
    player = YouTubePlayer(video, {
      videoId: 'fwXTzWlyA40',
      width: '100%',
      height: '100%'
    });

    player.on('stateChange', (event) => {
      playerState = event.data;
      console.log(event);
      if(event.data === 0) {
        stop();
      }
    });

    window.addEventListener('keydown', (event) => {
      console.log(event.key, playerState);
      if(event.key === 'Escape' && playerState > 0) {
        stop();
      }
    });
  }

  function setOpacity(opacity) {
    player.getIframe().then(iframe => {
      iframe.style.opacity = opacity;
    });
  }

  function play() {
    showVideo = true;
    setOpacity(1);
    player.playVideo();
  }

  function stop() {
    player.stopVideo();
    showVideo = false;
    setOpacity(0);
  }
</script>

<div
  bind:this={video}
  class='video'
  style={`opacity: ${showVideo ? '1' : '0'}`}
></div>

<div style={`opacity: ${showVideo ? '1' : '0'}`} class='button-video'>
  <Button on:click={stop} icon={IoMdClose} type='secondary'>
    CLOSE
  </Button>
</div>

<main style={`opacity: ${showVideo ? '0' : '1'}; pointer-events: ${showVideo ? 'none': 'auto'}`}>
  <header>
    <img id='logo' src='/logo.png' alt='Decorporation'>
    <h2>OUT NOW!</h2>
  </header>
  <div class='play' on:click={(e) => play()}>
    <button title='Play teaser'>
      <GoPlay />
    </button>
  </div>

  <div class='buttons'>
    <Button href='https://store.steampowered.com/app/1968950/Decorporation/' icon={FaSteam} type='primary'>
      BUY NOW - $2.99
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
  </div>
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

  .video {
    width: 100vw;
    height: 100vh;
    object-fit: cover;
    transition: opacity 0.1s;
    z-index: 0;
  }

  .button-video {
    position: fixed;
    top: 4vh;
    left: 0;
    right: 0;
    text-align: center;
  }

  /* .overlay {
    width: 100vw;
    height: 100vh;
    position: fixed;
    top: 0; left: 0;
    background: rgba(0, 0, 0, 0.3);
    z-index: 1;
    transition: opacity 0.1s;
  } */

  main {
    transition: opacity 0.1s;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
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

  .buttons {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    padding: 20px;
    text-align: center;
    z-index: 10;
  }
  .buttons a {
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
    z-index: 5;
  }

  .play button {
    background: transparent;
    border: none;
    color: #ccc;
    width: 50px;
    height: 50px;
    transition: color 0.1s;
    cursor: pointer;
  }

  .play button:hover {
    color: #bbb;
  }
</style>