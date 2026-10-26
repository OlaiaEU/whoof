<script lang="ts">
	const features = [
		{
			title: 'Zoomie detection',
			body: 'Every sprint around the sofa, with top speed and near-misses with the coffee table.'
		},
		{
			title: 'Sleep and recovery',
			body: 'Deep sleep, dream twitches and the 4pm sunbeam nap, distilled into one score out of 100.'
		},
		{
			title: 'Sniff analytics',
			body: 'Minutes spent investigating lampposts, ranked. The one on the corner remains undefeated.'
		},
		{
			title: 'Heart and breath',
			body: 'Resting heart rate and breathing around the clock, with a quiet nudge when something looks off.'
		},
		{
			title: 'Affection ledger',
			body: 'Every belly rub logged. Finally, objective proof of who in the house is the favourite human.'
		},
		{
			title: 'Lost Dog Mode',
			body: 'GPS wakes the moment they pursue a squirrel past the fence. Live map, loud ping, reunion.'
		}
	];
</script>

<section id="features" class="container">
	<h2 class="section-title">
		Everything your dog would tell you, <span class="soft">if they could stop sniffing for a second.</span>
	</h2>
	<div class="grid">
		{#each features as feature, i (feature.title)}
			<article>
				<p class="num">0{i + 1}</p>
				<h3>{feature.title}</h3>
				<p class="body">{feature.body}</p>
			</article>
		{/each}
	</div>
</section>

<style>
	section {
		padding-block: 120px;
	}

	h2 {
		margin-bottom: 64px;
		max-width: 820px;
	}

	.grid {
		display: flex;
		flex-wrap: wrap;
		gap: 0 48px;
	}

	article {
		flex: 1 1 320px;
		border-top: 1px solid var(--line);
		padding: 28px 0 40px;
	}

	.num {
		margin-bottom: 12px;
		font-family: var(--mono);
		font-size: 13px;
		color: var(--pine-text);
	}

	h3 {
		margin-bottom: 8px;
		font-weight: 500;
		font-size: 22px;
	}

	.body {
		color: var(--muted);
	}
</style>
