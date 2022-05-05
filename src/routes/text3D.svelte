<script>
  import { onMount } from 'svelte';
  import * as SC from 'svelte-cubed';
  import { FontLoader } from 'three/examples/jsm/loaders/FontLoader';
  import { TextGeometry } from 'three/examples/jsm/geometries/TextGeometry';
  import typeface from '@compai/font-mako/data/typefaces/mako-normal-400.json';

  let font;
  let text = "Test me out!!";
  let loader = new FontLoader();

  onMount(() => {
    font = loader.parse(typeface);
  })
</script>

<SC.Canvas alpha>
  <SC.Mesh
    geometry={ new TextGeometry(text, {
      font,
      size: 5,
      height: 10
    }) }
  />
  <SC.PerspectiveCamera position={[ 50, 50, 150 ]} />
  <SC.OrbitControls />
</SC.Canvas>

<label for="3DText">
  Enter text:
  <input id="3DText" name="3DText" type="text" bind:value={text} />
</label>

<style>
  label {
    position: absolute;
    top: 20%;
    right: 50%;
    z-index: 10;
  }
</style>