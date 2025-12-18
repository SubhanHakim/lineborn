<script>
	import Social from '../atoms/Social.svelte';
	import { TwitterIcon } from '@indaco/svelte-iconoir/twitter';
	import { TelegramIcon } from '@indaco/svelte-iconoir/telegram';
</script>

<div class="socials-container">

	<!-- Twitter (PUTIH) -->
	<Social tip="Twitter" link="https://x.com/lineborn_?s=11&t=p8y9jAhkYdmzWlb-DnEN9Q">
		<svg
			width="22"
			height="22"
			viewBox="0 0 24 24"
			fill="currentColor"
			xmlns="http://www.w3.org/2000/svg"
			class="icon"
		>
			<path d="M18.244 2H21.5l-7.78 9.02L23 22h-7.406l-5.8-7.29L3.6 22H.333l8.327-9.67L1 2h7.594l5.243 6.63L18.244 2zM16.848 20.1h2.227L7.25 3.8H5.024l11.824 16.3z"/>
		</svg>
	</Social>

	<!-- DexScreener (PUTIH) -->
	<Social tip="Pumpfun" link="https://pump.fun/coin/FBnZpnn7VPsgNnZfqEBN7EcVwQEwsBMr5HJDBmQYpump">
		<img src="/dexscreener.svg" alt="Pumpfun" class="icon icon-img" />
	</Social>

</div>

<style>
	.socials-container {
		display: flex;
		flex-direction: row;
		gap: 0.75rem;
		align-items: center;
	}

	/* SVG ICONS → WHITE */
	.icon {
		width: 22px;
		height: 22px;
		color: #ffffff !important;     /* <--- SVG putih */
		fill: #ffffff !important;      /* <--- override semua path */
		opacity: 0.95;
		transition: transform 0.2s ease;
	}

	/* IMG ICONS (Dexscreener) → MAKE WHITE via filter */
	.icon-img {
		filter: brightness(0) invert(1) !important;  /* <--- MAGIC: jadi putih */
	}

	.icon:hover {
		transform: scale(1.05);
		opacity: 1;
	}
</style>
