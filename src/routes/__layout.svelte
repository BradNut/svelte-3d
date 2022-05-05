<script>
  import '../app.css';
</script>

<header>
  <h1>Svelte 3D</h1>
  <nav>
    <a href="/cubes">Cubes</a>
    <a href="/star-canvas">Rotating Star</a>
    <a href="/playcube">Cube</a>
    <a href="/contributions">Contributions</a>
    <a href="/svg3D">SVG Example</a>
    <a href="/text3D">Text Example</a>
    <a href="/star">Star</a>
  </nav>
</header>

<main>
  <slot />
</main>

<style>
  :global(*, *::before, *::after) {
    margin: 0;
    box-sizing: inherit;
  }

  :global(html) {
    font-size: 62.5%;
    box-sizing: border-box;
  }

  :global(p) {
    word-wrap: normal;
    font-size: var(--bodyTextSize);
    color: var(--lightShade);
  }

  :global(li) {
    word-wrap: normal;
    font-size: var(--bodyTextSize);
    color: var(--lightShade);
  }

  header {
    display: flex;
    gap: 1rem;
    align-items: center;
    justify-content: space-between;
    width: 100vw;
    position: absolute;
    background: rgb(141, 153, 158);
    padding: 0.5rem;
    z-index: 10;
  }

  @media (max-width: 650px) {
    header {
      align-content: center;
      display: grid;
      justify-items: center;
      grid-template-columns: 1fr;
    }
  }

  nav {
    display: flex;
    align-items: center;
    justify-content: space-around;
    flex-wrap: wrap;
    gap: 0.6rem;
  }

  nav a {
    position: relative;
    font-size: var(--bodyTextSize);
    text-decoration: underline;
    color: var(--dark);
  }

  nav a:hover::after {
    transform: scale(1);
  }
</style>