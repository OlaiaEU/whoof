<script lang="ts">
	const plans = [
		{
			name: 'Good Boy',
			blurb: 'For the one-dog household.',
			price: '€79',
			terms: 'tag, then €4.99 / month',
			perks: ['1 Whoof Tag', 'Weekly Wag Report', 'Lost Dog Mode'],
			featured: false
		},
		{
			name: 'Pack Leader',
			blurb: 'For households that are mostly dog.',
			price: '€199',
			terms: '3 tags, then €9.99 / month',
			perks: ['Up to 3 Whoof Tags', 'Pack leaderboard (who walked most)', 'Vet sharing and health alerts'],
			featured: true
		}
	];
</script>

<section id="pricing" class="container">
	<h2 class="section-title">Two plans. <span class="soft">Treats sold separately.</span></h2>
	<div class="grid">
		{#each plans as plan (plan.name)}
			<div class="plan" class:featured={plan.featured}>
				<div class="top">
					<h3>{plan.name}</h3>
					{#if plan.featured}<p class="badge">Most wagged</p>{/if}
				</div>
				<p class="blurb">{plan.blurb}</p>
				<p class="price display">{plan.price}</p>
				<p class="terms">{plan.terms}</p>
				<ul>
					{#each plan.perks as perk (perk)}
						<li>{perk}</li>
					{/each}
				</ul>
				<a href="#preorder" class="btn choose">Choose {plan.name}</a>
			</div>
		{/each}
	</div>
</section>

<style>
	section {
		padding-bottom: 120px;
	}

	h2 {
		margin-bottom: 56px;
	}

	.grid {
		display: flex;
		flex-wrap: wrap;
		gap: 24px;
	}

	.plan {
		flex: 1 1 360px;
		border: 1px solid var(--line);
		border-radius: 28px;
		padding: 40px;
		background: var(--paper);
		display: flex;
		flex-direction: column;
	}

	.plan.featured {
		border-color: var(--pine);
		background: var(--pine);
		color: var(--linen);
	}

	.top {
		display: flex;
		justify-content: space-between;
		align-items: center;
		gap: 12px;
		flex-wrap: wrap;
		margin-bottom: 4px;
	}

	h3 {
		font-size: 22px;
		font-weight: 500;
	}

	.badge {
		padding: 4px 12px;
		border-radius: 999px;
		background: var(--accent);
		color: var(--ink);
		font-family: var(--mono);
		font-size: 12px;
		letter-spacing: 0.1em;
		text-transform: uppercase;
	}

	.blurb {
		margin-bottom: 32px;
		color: var(--muted);
	}

	.price {
		font-size: 64px;
	}

	.terms {
		margin: 6px 0 32px;
		color: var(--muted);
	}

	.featured .blurb,
	.featured .terms {
		color: var(--pine-muted);
	}

	ul {
		margin: 0 0 36px;
		padding-left: 18px;
		display: flex;
		flex-direction: column;
		gap: 8px;
		color: var(--ink-2);
		flex-grow: 1;
	}

	.featured ul {
		color: var(--pine-soft);
	}

	.choose {
		border-color: var(--ink);
		color: var(--ink);
	}

	.featured .choose {
		border-color: var(--linen);
		background: var(--linen);
		color: var(--pine);
	}

	@media (max-width: 560px) {
		.plan {
			padding: 28px;
		}
	}
</style>
