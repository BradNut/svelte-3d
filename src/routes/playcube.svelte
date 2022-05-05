<script>
  import * as THREE from 'three';
  import * as SC from 'svelte-cubed';
  import { spring } from 'svelte/motion';

  let width = 1;
  let height = 1;
  let depth = 1;

  let spin = 0;
  let isActive = false;

  let xPos = spring(0);
  $: $xPos = isActive ? 10 : 0;
</script>

<svelte:window on:click={() => { isActive = !isActive }} />

<div class="controls">
  <h1>Modify Cube Size:</h1>
  <label for="width">Width:
    <input id="width" name="width" type="range" min={0.1} max={3} step={0.1} bind:value={width} />
  </label>
  <label for="height">Height:
    <input id="height" name="height" type="range" min={0.1} max={3} step={0.1} bind:value={height} />
  </label>
  <label for="depth">Depth:
    <input id="depth" name="depth" type="range" min={0.1} max={3} step={0.1} bind:value={depth} />
  </label>
</div>

<SC.Canvas antialias background={new THREE.Color('grey')}>
  <SC.Mesh
    position={[$xPos, 0, 0]}
    rotation={[0, spin, 0]}
    scale={[width, height, depth]}
    material={new THREE.MeshStandardMaterial({ color: 'purple' })}
    geometry={new THREE.BoxGeometry()}
  />
  <SC.PerspectiveCamera position={[2, 2, 2]} />
  <SC.OrbitControls />
  <SC.AmbientLight intensity={0.5} />
  <SC.DirectionalLight intensity={1} position={[3, 5, -4]} />
</SC.Canvas>

<style>
  .controls {
    display: grid;
    gap: 2rem;
    bottom: 0;
    margin: 2rem;
    position: absolute;
    z-index: 10;
  }
  label {
    font-size: var(--bodyTextSize);
    display: flex;
    place-content: center;
    place-items: center;
  }
</style>