<script>
  import * as SC from 'svelte-cubed';
  import * as THREE from 'three';
  import * as PE from 'svelte-cannon';

  const position = PE.writableVec3(0,5,0);
</script>

<PE.Body mass={1} bind:position={$position}>
  <PE.Box size={[1,1,1]} />
</PE.Body>

<SC.Mesh geometry={new THREE.BoxGeometry()} position={$position.toArray()} />