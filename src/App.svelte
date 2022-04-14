<script>
  // import logo from './assets/logo.png';
</script>

<header>
  <img id='logo' src='/logo.png' alt='Decorporation'>
  <h2>COMING SOON</h2>
</header>

<main>
  <a href='https://store.steampowered.com/app/1968950/Decorporation/'>
    <img src='/steam.svg' alt='Steam'>
    STEAM
  </a>
  <a href='https://twitter.com/DecorpGame'>
    <img src='/twitter.svg' alt='Twitter'>
    TWITTER
  </a>
  <a href='#'>
    <img src='/discord.svg' alt='Discord'>
    DISCORD
  </a>
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
    padding: 50px;
    text-align: center;
  }

  main a {
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
  main a img {
    width: 20px;
    margin-right: 10px;
  }
  main a:hover {
    background: #aaaaaa;
  }
</style>