x<script>
  import { onMount } from 'svelte';
  import * as SC from 'svelte-cubed';
  import * as THREE from 'three';
  import { SVGLoader } from 'three/examples/jsm/loaders/SVGLoader';
  import logo from '$lib/logo.svg?raw';

  const svgLogo = new SVGLoader().parse(logo);
  
  let x = Math.PI;
  let y = 0;
  let z = 0;
</script>

<SC.Canvas alpha>
  <SC.Group scale={0.05} rotation={[x, y, z]}>
    {#each svgLogo.paths as logoPath}
      <SC.Mesh
        geometry={new THREE.ExtrudeGeometry(logoPath.toShapes(false), {
          depth: 40
        })}
      />
    {/each}
  </SC.Group>
  <SC.PerspectiveCamera position={[ 10, 0, 100 ]} />
  <SC.OrbitControls />
</SC.Canvas>

<div class="controls">
  <h1>Rotation Controls:</h1>
  <label for="x">X: <input id="x" name="x" type="range" bind:value={x} min={0} max={5} step={0.01} /></label>
  <label for="y">Y: <input id="y" name="y" type="range" bind:value={y} min={0} max={5} step={0.01} /></label>
  <label for="z">Z: <input id="z" name="z" type="range" bind:value={z} min={0} max={5} step={0.01} /></label>
</div>

<style>
  .controls {
    display: grid;
    gap: 1rem;
    position: absolute;
    bottom: 0%;
    margin: 1rem;
    z-index: 10;
  }
</style>