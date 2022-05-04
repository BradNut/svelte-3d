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
  <SC.Group position={[ 0, -2, 0 ]}>
    <SC.Mesh
      geometry={new THREE.PlaneGeometry(100,100)}
      material={new THREE.MeshStandardMaterial({ color: 'grey' })}
      rotation={[-Math.PI / 2, 0, 0]}
    />
    <SC.Primitive
      position={[ 0, 0.001, 0]}
      object={new THREE.GridHelper(100, 100, 0x444444, 0x555555)}
    />
  </SC.Group>
  <SC.PerspectiveCamera position={[3, 3, 3]} />
  <SC.OrbitControls />
  <SC.AmbientLight intensity={1} />
  <SC.DirectionalLight intensity={0.7} />
  <SC.PointLight intensity={1} position={[2, 5, 2]} />
</SC.Canvas>

<style>
  .controls {
    position: absolute;
    z-index: 10;
  }
</style>
