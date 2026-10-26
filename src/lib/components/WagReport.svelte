<script lang="ts">
	import DogAvatar from './dogs/DogAvatar.svelte';

	const metrics = [
		{ label: 'Recovery', value: '91', highlight: true },
		{ label: 'Steps', value: '58,904' },
		{ label: 'Zoomies', value: '17' }
	];

	const days = [
		{ day: 'M', steps: 55 },
		{ day: 'T', steps: 100 },
		{ day: 'W', steps: 62 },
		{ day: 'T', steps: 48 },
		{ day: 'F', steps: 70 },
		{ day: 'S', steps: 84 },
		{ day: 'S', steps: 40 }
	];
	const best = Math.max(...days.map((d) => d.steps));
</script>

<section id="app">
	<div class="container inner">
		<div class="copy">
			<p class="eyebrow">The app</p>
			<h2 class="section-title">The Wag Report.</h2>
			<p>
				Every Sunday, a short read on how the week went: activity, rest, heart health, and the
				moments worth celebrating.
			</p>
			<p>
				Spot a slow week early, or simply enjoy confirmation that Tuesday's park trip was,
				statistically, legendary.
			</p>
		</div>

		<div class="card">
			<div class="head">
				<DogAvatar breed="golden" size={52} />
				<div>
					<p class="name">Biscuit's week</p>
					<p class="dates">05 – 11 OCT</p>
				</div>
			</div>

			<div class="metrics">
				{#each metrics as metric (metric.label)}
					<div>
						<p class="metric-label">{metric.label}</p>
						<p class="metric-value" class:highlight={metric.highlight}>{metric.value}</p>
					</div>
				{/each}
			</div>

			<div class="chart" role="img" aria-label="Daily steps bar chart, highest on Tuesday">
				{#each days as d, i (i)}
					<div class="bar" class:best={d.steps === best} style:height="{d.steps}%"></div>
				{/each}
			</div>
			<div class="days" aria-hidden="true">
				{#each days as d, i (i)}
					<span>{d.day}</span>
				{/each}
			</div>

			<p class="verdict">Biscuit was 23% more good boy than last week.</p>
		</div>
	</div>
</section>

<style>
	section {
		background: var(--sand);
	}

	.inner {
		padding-block: 120px;
		display: flex;
		flex-wrap: wrap;
		align-items: center;
		gap: 64px;
	}

	.copy {
		flex: 1 1 400px;
		min-width: 0;
	}

	.copy .eyebrow {
		margin-bottom: 20px;
	}

	.copy h2 {
		margin-bottom: 24px;
	}

	.copy p:not(.eyebrow) {
		font-size: 19px;
		color: var(--ink-2);
	}

	.copy p + p:not(.eyebrow) {
		margin-top: 16px;
	}

	.card {
		flex: 1 1 440px;
		min-width: 0;
		background: var(--paper);
		border-radius: 28px;
		padding: 32px;
		box-shadow: 0 24px 60px rgba(34, 32, 28, 0.1);
	}

	.head {
		display: flex;
		align-items: center;
		gap: 14px;
		margin-bottom: 28px;
	}

	.name {
		font-family: var(--serif);
		font-size: 28px;
		line-height: 1.1;
	}

	.dates,
	.metric-label,
	.days {
		font-family: var(--mono);
		font-size: 12px;
		color: var(--muted);
	}

	.metrics {
		display: flex;
		flex-wrap: wrap;
		gap: 24px;
		margin-bottom: 32px;
	}

	.metrics > div {
		flex: 1 1 110px;
	}

	.metric-label {
		letter-spacing: 0.1em;
		text-transform: uppercase;
	}

	.metric-value {
		margin-top: 4px;
		font-size: 34px;
		font-weight: 500;
	}

	.metric-value.highlight {
		color: var(--pine-text);
	}

	.chart {
		display: flex;
		align-items: flex-end;
		gap: 14px;
		height: 150px;
		border-bottom: 1px solid var(--line);
	}

	.bar {
		flex: 1;
		background: var(--line);
		border-radius: 6px 6px 0 0;
	}

	.bar.best {
		background: var(--pine);
	}

	.days {
		display: flex;
		gap: 14px;
		margin-top: 10px;
		text-align: center;
	}

	.days span {
		flex: 1;
	}

	.verdict {
		margin-top: 28px;
		padding-top: 20px;
		border-top: 1px solid var(--line);
		font-family: var(--serif);
		font-style: italic;
		font-size: 22px;
		line-height: 1.3;
		color: var(--ink-2);
	}

	@media (max-width: 560px) {
		.card {
			padding: 24px;
		}
	}
</style>
