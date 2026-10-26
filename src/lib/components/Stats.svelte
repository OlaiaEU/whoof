<script lang="ts">
	const stats = [
		{ label: 'Battery', value: '14 days' },
		{ label: 'Weight', value: '9 g' },
		{ label: 'Sensors', value: '6' },
		{ label: 'Cats supported', value: '0' }
	];
</script>

<section>
	<dl class="container">
		{#each stats as stat (stat.label)}
			<div>
				<dt class="eyebrow">{stat.label}</dt>
				<dd class="display">{stat.value}</dd>
			</div>
		{/each}
	</dl>
</section>

<style>
	section {
		border-block: 1px solid var(--line);
	}

	dl {
		margin-block: 0;
		padding-block: 40px;
		display: flex;
		flex-wrap: wrap;
		gap: 32px;
	}

	dl > div {
		flex: 1 1 200px;
	}

	dt {
		letter-spacing: 0.1em;
	}

	dd {
		margin-top: 6px;
		font-size: 48px;
	}
</style>
