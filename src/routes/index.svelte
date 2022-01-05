<script context="module" lang="ts">
	import SlideContainer from '../components/SlideContainer.svelte';
	import Slide from '../components/Slide.svelte';
	import type SlideData from '../Typescript/SlideData';
	import { getContext } from 'svelte';

	const slides: SlideData[] = [
		{title: 'test'},
		{title: 'test2'},
	];
</script>

<SlideContainer>
	{#each slides as data, index}
		<Slide slideData={Object.assign(data, {slideIndex: getContext('SetIndex').index()})} />
	{/each}
</SlideContainer>
