<script context='module' lang='ts'>
	import SlideContainer from '../components/SlideContainer.svelte';
	import Slide from '../components/Slide.svelte';
	import Menu from '../components/Menu.svelte';
	import type SlideData from '../Typescript/SlideData';
	import { getContext } from 'svelte';
	import ApplicationModes from '../Typescript/ApplicationModes';

	let mode: ApplicationModes = ApplicationModes.Menu;
	let editingFile: string|null = null;


	const slides: SlideData[] = [
		{ title: 'test' },
		{ title: 'test2' }
	];
</script>

<script lang="ts">
	import { setContext } from 'svelte';
	import type ApplicationModes from '../Typescript/ApplicationModes.js';

	setContext('AppState', {
		currentMode: () => mode,
		setMode: (to: ApplicationModes) => mode = to,
		setFile: (path: string) => editingFile = path
	})
</script>

{#if mode === ApplicationModes.Menu}
	<Menu />
{:else if mode === ApplicationModes.Edit}
	ewa
{:else if mode === ApplicationModes.Presentation}
	<SlideContainer>
		{#each slides as data, index}
			<Slide slideData={Object.assign(data, {slideIndex: getContext('SetIndex').index()})} />
		{/each}
	</SlideContainer>
{/if}
