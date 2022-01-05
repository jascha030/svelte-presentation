<script lang='ts'>
	import { getContext } from 'svelte';
	import ApplicationModes from '../Typescript/ApplicationModes';

	let { setMode } = getContext('AppState');

	const triggerFile = () => (document.querySelector('#file-selector') as HTMLInputElement).click();
	const startNew = () => setMode(ApplicationModes.Edit);
</script>

<div class='menu'>
	<div class='menu-heading main'>
		<h1>🎁 Present</h1>
	</div>
	<div class='menu-content main'>
		<ul>
			<li on:click={startNew}>
				<svg xmlns='http://www.w3.org/2000/svg' class='h-8 w-8' fill='none' viewBox='0 0 24 24' stroke='currentColor'>
					<path stroke-linecap='round' stroke-linejoin='round' stroke-width='2'
								d='M13 9l3 3m0 0l-3 3m3-3H8m13 0a9 9 0 11-18 0 9 9 0 0118 0z' />
				</svg>
				New presentation
			</li>
			<li on:click={triggerFile}>
				<svg xmlns='http://www.w3.org/2000/svg' class='h-8 w-8' fill='none' viewBox='0 0 24 24' stroke='currentColor'>
					<path stroke-linecap='round' stroke-linejoin='round' stroke-width='2'
								d='M13 9l3 3m0 0l-3 3m3-3H8m13 0a9 9 0 11-18 0 9 9 0 0118 0z' />
				</svg>
				Open presentation
			</li>
		</ul>

		<form id='file-selector-form' action='#' enctype='multipart/form-data'>
			<input id='file-selector' type='file' name='selected-file' accept='text/markdown'>
		</form>
	</div>
</div>

<style lang='scss'>
  .menu {
    @apply w-screen h-screen flex justify-center align-middle items-center flex-col;

    background: #212431;
  }

  .menu-heading {
    @apply text-center text-white drop-shadow-sm;

    h1 {
      @apply text-9xl mb-16;
    }
  }

  .menu-content {
    @apply text-center text-white text-3xl;

    ul {
      @apply text-left;

      li {
        @apply my-16 cursor-pointer transition-all duration-100 ease-in-out justify-center flex;

        &:hover {
          @apply pl-2 text-slate-200;
        }
      }
    }
  }

  #file-selector-form {
    display: none;
  }
</style>
