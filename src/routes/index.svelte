<script>
  import * as SC from 'svelte-cubed';
  import * as THREE from 'three';
  import * as PE from 'svelte-cannon';
  import Box from '$lib/Box.svelte';
</script>

<PE.World gravity={[0, -9.8 ,0]}>
  <SC.Canvas antialias shadows>
    <PE.Body mass={0} rotation={[-Math.PI / 2, 0, 0]}>
      <PE.Plane />
    </PE.Body>
    <SC.Mesh
      geometry={new THREE.PlaneGeometry(50, 50)}
      rotation={[-Math.PI / 2, 0, 0]}
      material={new THREE.MeshStandardMaterial({ color: "grey"})}
    />
    <Box />
    <SC.AmbientLight intensity={1} />
    <SC.PerspectiveCamera position={[ 2, 2, 15 ]} target={[0,0,0]} />
  </SC.Canvas>
</PE.World>