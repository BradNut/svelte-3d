<script>
  import * as SC from 'svelte-cubed';
  import * as THREE from 'three';
  import * as PE from 'svelte-cannon';
  import * as CANNON from 'cannon-es';

  const position = PE.writableVec3(0, 5, 0);
  let rotation = PE.writableVec3(0, 0, 0);
  let velocity = new CANNON.Vec3(1, 1, 1);
</script>

<PE.Body on:collide={(e) => console.log(e)} mass={1} bind:position={$position} bind:rotation={$rotation} {velocity}>
  <PE.Box size={[0.5,0.5,0.5]} />
</PE.Body>

<SC.Mesh
  castShadow
  rotation={$rotation.toArray()}
  geometry={new THREE.BoxGeometry()}
  position={$position.toArray()}
/>