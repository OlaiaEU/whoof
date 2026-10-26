<script lang="ts">
	const faqs = [
		{
			q: 'Does it work on cats?',
			a: 'We tried. The cats declined to participate and knocked the prototype off a table.'
		},
		{
			q: 'How long does the battery last?',
			a: 'About 14 days per charge. The dock is shaped like a small bone, so nobody forgets where it is.'
		},
		{
			q: 'Is it waterproof?',
			a: 'Rain, puddles, the sea, and that one pond you told them not to go in. All fine.'
		},
		{
			q: 'What size dogs does it fit?',
			a: 'Chihuahua to Great Dane. The tag weighs less than a large treat.'
		}
	];
</script>

<section class="container">
	<h2 class="display">Questions, fetched.</h2>
	<div class="list">
		{#each faqs as faq (faq.q)}
			<details>
				<summary>{faq.q}</summary>
				<p>{faq.a}</p>
			</details>
		{/each}
	</div>
</section>

<style>
	section {
		max-width: 820px;
		padding-bottom: 120px;
	}

	h2 {
		margin-bottom: 32px;
		font-size: clamp(36px, 4vw, 52px);
	}

	.list {
		border-bottom: 1px solid var(--line);
	}

	details {
		border-top: 1px solid var(--line);
		padding: 22px 0;
	}

	summary {
		cursor: pointer;
		font-size: 19px;
		font-weight: 500;
	}

	details p {
		margin-top: 12px;
		color: var(--muted);
	}
</style>
