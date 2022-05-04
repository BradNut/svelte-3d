<script>
  import * as THREE from 'three';
  import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader';
  import * as SC from 'svelte-cubed';
  let star;
  let loader = new GLTFLoader();

  loader.load('star.gltf', (gltf) => {
    star = gltf.scene.children[0].geometry;
  });
</script>

<SC.Canvas antialias alpha>
  <SC.Mesh
    geometry={star}
    rotation={[-90, 0, 0]}
    material={new THREE.MeshStandardMaterial({
      color: 0xffff00,
      roughness: 0,
      metalness: 0.7,
    })}
  />
  <SC.PerspectiveCamera position={[3, 3, 3]} />
  <SC.OrbitControls />
  <SC.AmbientLight intensity={1} />
  <SC.DirectionalLight intensity={0.5} position={[-3, 5, 7]} />
</SC.Canvas>

<style>
  .controls {
    position: absolute;
    z-index: 10;
  }
</style>
