<script>
	import { CircleBufferGeometry, MeshStandardMaterial, BoxBufferGeometry, DoubleSide } from 'three';
	import { Mesh, Group } from 'threlte';
	import { onMount, onDestroy } from 'svelte';
	import { tweened } from 'svelte/motion';
	import { cubicOut } from 'svelte/easing';

	const scale = tweened(0, {
		duration: 1100,
		easing: cubicOut
	});

	onMount(() => {
		scale.set(1);
	});

	onDestroy(() => {
		scale.set(0);
	});

	let boardColor = '#615958';
</script>

<Group>
	<Mesh
		castShadow
		geometry={new BoxBufferGeometry(0.15, $scale * 2.8, 0.15)}
		position={{ x: 0.5 }}
		material={new MeshStandardMaterial({ color: boardColor })}
	/>
	<Mesh
		castShadow
		geometry={new BoxBufferGeometry(0.15, $scale * 2.8, 0.15)}
		position={{ x: -0.5 }}
		material={new MeshStandardMaterial({ color: boardColor })}
	/>
	<Mesh
		castShadow
		geometry={new BoxBufferGeometry($scale * 2.8, 0.15, 0.15)}
		position={{ y: 0.5 }}
		material={new MeshStandardMaterial({ color: boardColor })}
	/>
	<Mesh
		castShadow
		position={{ y: -0.5 }}
		geometry={new BoxBufferGeometry($scale * 2.8, 0.15, 0.15)}
		material={new MeshStandardMaterial({ color: boardColor })}
	/>
</Group>
