<script>
  import * as THREE from 'three';
  import { GLTFLoader } from 'three/examples/jsm/loaders/GLTFLoader';
  import * as SC from 'svelte-cubed';
  let star;
  let rotation = 0;

  let loader = new GLTFLoader();
  loader.load('star.gltf', (gltf) => {
    star = gltf.scene.children[0].geometry;
  });

  SC.onFrame(() => {
    rotation += 0.01
  })
</script>

<div class="star-container">
  <SC.Canvas antialias alpha>
    <SC.Mesh
      geometry={star}
      rotation={[-90, 0, rotation]}
      material={new THREE.MeshStandardMaterial({
        color: 0xffff00,
        roughness: 0,
        metalness: 0.7,
      })}
    />
    <SC.PerspectiveCamera position={[3, 1, 3]} />
    <SC.AmbientLight intensity={1} />
    <SC.DirectionalLight intensity={0.7} />
    <SC.PointLight intensity={1} position={[2, 5, 2]} />
  </SC.Canvas>
</div>

<style>
  .star-container {
    position: relative;
    width: 100px;
    height: 100px;
  }
</style>
