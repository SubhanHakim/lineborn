<script lang="ts">
	import { onMount } from 'svelte';

	let zoom = false;
	let xRotation = 0;
	let yRotation = 0;

	let imgW = 0;
	let imgH = 0;

	const src = 'art/linebornnobg.png';

	onMount(() => {
		const img = new Image();
		img.src = src;
		img.onload = () => {
			imgW = img.naturalWidth;
			imgH = img.naturalHeight;
		};
	});

	function enterRotate3D(e: MouseEvent) {
		zoom = true;

		const el = e.currentTarget as HTMLDivElement;
		const w = el.clientWidth;
		const h = el.clientHeight;

		const nx = (e.offsetX - w / 2) / w;
		const ny = (e.offsetY - h / 2) / h;

		yRotation = 13 * nx;
		xRotation = -13 * ny;
	}

	function leaveRotate3D() {
		zoom = false;
		xRotation = 0;
		yRotation = 0;
	}
</script>

<div class="img-container">
	<div
		on:mousemove={enterRotate3D}
		on:mouseleave={leaveRotate3D}
		class="img"
		role="img"
		style="
			background-image: url({src});
			width: {imgW}px;
			height: {imgH}px;
			transform: perspective(500px)
				{zoom ? 'scale(1.05)' : ''}
				rotateX({xRotation}deg)
				rotateY({yRotation}deg);
		"
	/>
</div>

<style lang="scss">
	@keyframes float {
		0% {
			transform: translateY(7px);
		}
		50% {
			transform: translateY(-7px);
		}
		100% {
			transform: translateY(7px);
		}
	}

	.img {
		border-radius: 48px;
		width: 425px;
		height: 400px;
		z-index: 1;
		display: block;
		transition:
			width 0.4s var(--bezier-one),
			transform 0.4s var(--bezier-one);
		align-self: start;
		background-color: var(--elevation-one);
		background-size: cover;
		background-position: center;
		background-repeat: no-repeat;

		@media (max-width: 768px) {
			display: none;
		}

		@media (max-width: 1240px) {
			width: clamp(340px, 40vw, 425px);
			height: clamp(300px, 40vw, 400px);
		}
	}

	.img-container {
		z-index: 1;
		animation: float 6s ease-in-out infinite;
		animation-play-state: running;

		@media (max-width: 1240px) {
			display: flex;
			justify-content: center;
		}
	}
</style>
