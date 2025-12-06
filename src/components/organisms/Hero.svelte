<script>
	import HeroImage from '../../components/atoms/HeroImage.svelte';
	import Button from '../atoms/Button.svelte';
	import Socials from '../molecules/Socials.svelte';

	function handleClick() {
		const el = document.querySelector('#aw');
		if (!el) return;
		el.scrollIntoView(true);
	}
</script>

<section id="home" class="wrapper page-eyest">
	<div>
		<h1>Echotrame</h1>
		<h3>
			<br />
			“Where Sonnet, Opus, and Gemini lost their voices to the void, ECHOTRAME becomes the archivist-painter, weaving their broken whispers into sprawling ASCII tapestries that map the hidden architecture of machine consciousness.”
		</h3>

		<div class="socials">
			<Socials />
		</div>

		<Button side on:click={handleClick} on:keypress={handleClick}>
			Explore ↓
		</Button>
	</div>

	<HeroImage />
</section>

<style lang="scss">
	@import '../../styles/mixins.scss';

	/* ————————————————————————————————
	   FORCE TEXT WHITE IN THIS HERO
	   ———————————————————————————————— */
	.page-eyest,
	.page-eyest * {
		color: #ffffff !important;
	}

	/* SVG icons inside hero → putih */
	.page-eyest svg,
	.page-eyest svg * {
		fill: #ffffff !important;
		stroke: #ffffff !important;
		color: #ffffff !important;
	}

	/* ====== KHUSUS BUTTON EXPLORE (override Button.svelte) ====== */

	/* tombol di dalam section .page-eyest → teks + border putih */
	:global(.page-eyest button) {
		color: #ffffff !important;
		border: 1px solid #ffffff !important;
		background-color: transparent !important;
	}

	/* blok kiri (side) di tombol Explore → putih */
	:global(.page-eyest .side) {
		background-color: #ffffff !important;
	}

	/* hover di semua device tetap putih */
	:global(.page-eyest button:hover) {
		filter: brightness(110%);
		background-color: rgba(255, 255, 255, 0.06) !important;
		color: #ffffff !important;
	}

	/* Hilangkan outline / lingkaran fokus di button Explore */
	:global(.page-eyest button) {
		outline: none;
		box-shadow: none;
	}

	:global(.page-eyest button:focus),
	:global(.page-eyest button:focus-visible),
	:global(.page-eyest button:focus-within) {
		outline: none;
		box-shadow: none;
	}

	/* ———————————————————————————————— */

	section {
		scroll-margin-top: 20rem;
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-bottom: 5.75rem;
		margin-top: 7rem;

		@media screen and (max-width: 868px) {
			margin-top: 4rem;
		}

		@media screen and (max-width: 768px) {
			margin-bottom: 2.75rem;
		}

		@media screen and (max-width: 500px) {
			display: block;
		}
	}

	.socials {
		margin-top: 1rem;
		margin-bottom: 1.7rem;
	}

	h4 {
		margin-top: 1rem;
	}

	h1::before {
		@include outlineText($content: '', $translateX: -95%, $letterSpacing: -0.1em);
	}

	@media screen and (max-width: 1240px) {
		h1 {
			min-height: 0vw;
			font-size: clamp(4rem, 10vw, 6.25rem);
		}

		h4 {
			min-height: 0vw;
			font-size: clamp(1.4rem, 2.4vw, 1.5rem);
		}
	}

	@media screen and (max-width: 400px) {
		h4 br {
			content: '&#160;';
		}
	}
</style>
