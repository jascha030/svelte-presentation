<script>
	import { setContext } from 'svelte';

	let startIndex = -1;
	let currentIndex = 0;

	setContext('SetIndex', {
		index: () => {
			startIndex++;

			return startIndex;
		},
		current: () => currentIndex,
	});

	const next = () => {
		if (currentIndex < startIndex) {
			currentIndex++;

			let activeSlide = document.querySelector('.slide.translate-x-0');

			activeSlide.classList.remove('translate-x-0');
			activeSlide.classList.add('-translate-x-full');

			let nextSlide = activeSlide.nextElementSibling;

			nextSlide.classList.remove('translate-x-full');
			nextSlide.classList.add('translate-x-0');
		}

	};

	const prev = () => {
		if (currentIndex > 0) {
			currentIndex--;

			let activeSlide = document.querySelector('.slide.translate-x-0');
			activeSlide.classList.remove('translate-x-0');
			activeSlide.classList.add('translate-x-full');

			let previousSlide = activeSlide.previousElementSibling;

			previousSlide.classList.remove('-translate-x-full');
			previousSlide.classList.add('translate-x-0');
		}
	};
</script>

<div class='presentation-container'>
	<div class='slide-container'>
		<slot>
		</slot>
	</div>
	<div class='slide-controls'>
		<div class='presentation-control prev' on:click={() => prev()}>
			<svg xmlns='http://www.w3.org/2000/svg' class='h-20 w-20' fill='none' viewBox='0 0 24 24' stroke='currentColor'>
				<path stroke-linecap='round' stroke-linejoin='round' stroke-width='2'
							d='M11 15l-3-3m0 0l3-3m-3 3h8M3 12a9 9 0 1118 0 9 9 0 01-18 0z' />
			</svg>
		</div>

		<div class='presentation-display'>
			{ currentIndex + 1 } /
			{#if startIndex === -1}
				0
			{:else}
				{startIndex + 1}
			{/if}
		</div>

		<div class='presentation-control next' on:click={() => next()}>
			<svg xmlns='http://www.w3.org/2000/svg' class='h-20 w-20' fill='none' viewBox='0 0 24 24' stroke='currentColor'>
				<path stroke-linecap='round' stroke-linejoin='round' stroke-width='2'
							d='M13 9l3 3m0 0l-3 3m3-3H8m13 0a9 9 0 11-18 0 9 9 0 0118 0z' />
			</svg>
		</div>
	</div>
</div>

<style lang='postcss'>
    .presentation-container {
        /*bg-gradient-to-br from-orange-600 to-orange-500*/
        @apply w-screen h-screen bg-gradient-to-br from-orange-400 to-orange-300;
    }

    .slide-container {
        @apply relative;
    }

    .slide-controls {
        @apply absolute bottom-0 left-0 right-0 flex justify-center content-center flex-row h-28;
    }

    .presentation-display {
        @apply flex content-center justify-center;
    }

    .presentation-control {
        @apply flex transition-all duration-150 ease-in-out grow justify-center content-center text-xl text-slate-300 opacity-5;
    }

    .presentation-control svg {
        @apply origin-center transition-all duration-150 ease-in-out;
    }

    .presentation-control:hover {
        @apply text-slate-500 cursor-pointer opacity-100;
    }

    .prev svg, .next svg {
        @apply pt-4;
    }

    .prev:hover svg {
        @apply pr-4;
    }

    .next:hover svg {
        @apply pl-4;
    }
</style>
