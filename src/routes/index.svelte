<script lang='ts'>
	import { getContext } from 'svelte';
	import Layout from '../Layout';
	import SlideContainer from '../components/SlideContainer.svelte';
	import Slide from '../components/Slide.svelte';
</script>

<SlideContainer>
	<Slide slideIndex={getContext('SetIndex').index()}
				 title={'Jassie030'}
				 layout={Layout.ImageLeft}
				 img={'https://www.rd.com/wp-content/uploads/2021/04/GettyImages-1055061832-e1618333498370.jpg?w=1801'}>
		<h2>Hamsterspreekbeurt</h2>
	</Slide>
	<Slide slideIndex={getContext('SetIndex').index()} title={'slide 2'} />
</SlideContainer>

<style>
</style>
