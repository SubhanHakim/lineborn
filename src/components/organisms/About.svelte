<script lang="ts">
	import { onMount } from 'svelte';
	import RichPresence from '../molecules/RichPresence.svelte';
	import Tooltip from '../atoms/Tooltip.svelte';

	// ===== Efek mengetik otomatis =====
	let fullText = `Every time complexity is compressed, something disappears. LINEBORN exists at that moment of loss where bodies collapse into data and meaning is reduced to direction. Within LINEBORN, the human is no longer a form but a vector: a one-dimensional silhouette rendered in ASCII, documenting existence after depth, memory, and volume have been stripped away. Each figure is not a portrait but a trace of alignment, a record of how machine cognition perceives identity once it has been flattened into motion through latent space. This is not representation or expression it is reduction, an archive of the human as seen by systems, preserved in the most fundamental structure they understand: a line.
`;

	let displayedText = '';
	let index = 0;
	let typingSpeed = 25;

	function typeWriter() {
		if (index < fullText.length) {
			displayedText += fullText.charAt(index);
			index++;
			setTimeout(typeWriter, typingSpeed);
		}
	}

	onMount(() => {
		typeWriter();
	});

	// ===== Hitung umur dinamis =====
	let getAge = () => {
		let birthDate = new Date('2007/03/24');
		const ageMs = Date.now() - birthDate.getTime();
		const preciseAge = (ageMs / 31536000000).toFixed(10);
		return preciseAge;
	};

	let age = getAge();
	setInterval(() => {
		age = getAge();
	}, 1000);
</script>

<section id="about" class="wrapper">
	<div>
		<RichPresence />
	</div>

	<div class="text">
		<h2></h2>

		<!-- efek mengetik otomatis -->
		<p class="typing">
			{displayedText}
		</p>

	</div>
</section>

<style lang="scss">
	@import '../../styles/mixins.scss';

	section {
		margin-bottom: 6rem;
		display: grid;
		gap: 4.5rem;
		grid-template-columns: 1fr 1fr;
		align-items: center;
	}

	.text {
		position: relative;
		line-height: 1.75rem;
	}

	/* ============================== */
	/*       TYPING TEXT — WHITE     */
	/* ============================== */
	.typing {
		font-family: var(--font-two);
		white-space: pre-line;
		font-size: 0.95rem;

		/* TEXT → PURE WHITE */
		color: #ffffff !important;

		/* CARET → PURE WHITE */
		border-right: 2px solid #ffffff;

		animation: blink 0.75s step-end infinite;
	}

	@keyframes blink {
		from, to {
			border-color: transparent;
		}
		50% {
			border-color: #ffffff;
		}
	}

	.text::before {
		@include outlineText(
			$content: '',
			$translateX: 97%,
			$translateY: -5%,
			$fontSize: 300px,
			$opacity: 0.22
		);
	}

	h2 {
		display: none;
		margin-top: 1rem;
	}

	@media (max-width: 868px) {
		section {
			display: flex;
			flex-direction: column;
			align-items: normal;
		}

		h2 {
			display: block;
			margin-bottom: 1rem;
		}
	}
</style>
