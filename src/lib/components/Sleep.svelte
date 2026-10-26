<script lang="ts">
	import DogSleeping from './dogs/DogSleeping.svelte';

	const pills = ['Deep sleep 6h 40m', 'Dream twitches 14', 'Snoring: tolerable'];
</script>

<section class="container">
	<div class="card">
		<div class="copy">
			<p class="eyebrow">Sleep tracking</p>
			<h2 class="section-title">Professional napper. <em>Now with data.</em></h2>
			<p class="body">
				Luna sleeps sixteen hours a day. Whoof knows which ones were deep, which had dreams, and
				which were the strategic sofa kind.
			</p>
		</div>
		<div class="visual">
			<DogSleeping />
			<ul class="pills">
				<li class="pill pill-strong">Nap score 91</li>
				{#each pills as pill (pill)}
					<li class="pill">{pill}</li>
				{/each}
			</ul>
		</div>
	</div>
</section>

<style>
	section {
		padding-block: 112px;
	}

	.card {
		background: var(--paper);
		border-radius: 32px;
		padding: 56px 40px 40px;
		display: flex;
		flex-wrap: wrap;
		align-items: center;
		gap: 40px;
	}

	.copy {
		flex: 1 1 340px;
		min-width: 0;
	}

	.eyebrow {
		margin-bottom: 16px;
	}

	h2 {
		margin-bottom: 20px;
		font-size: clamp(40px, 5vw, 64px);
	}

	h2 em {
		color: var(--pine-text);
	}

	.body {
		font-size: 19px;
		color: var(--ink-2);
		max-width: 420px;
	}

	.visual {
		flex: 1 1 520px;
		min-width: 0;
	}

	.pills {
		list-style: none;
		margin: 16px 0 0;
		padding: 0;
		display: flex;
		flex-wrap: wrap;
		gap: 10px;
	}

	.pill {
		padding: 8px 14px;
		border-radius: 999px;
		background: var(--sand);
		font-size: 14px;
	}

	.pill-strong {
		background: var(--pine);
		color: var(--linen);
	}

	@media (max-width: 560px) {
		.card {
			padding: 40px 24px 24px;
		}
	}
</style>
