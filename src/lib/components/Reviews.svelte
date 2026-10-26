<script lang="ts">
	import DogAvatar from './dogs/DogAvatar.svelte';

	const reviews = [
		{
			breed: 'golden',
			quote: 'Finally, hard data that I am a good boy. I would like this framed.',
			name: 'Biscuit',
			details: 'Golden Retriever, 4'
		},
		{
			breed: 'dachshund',
			quote: 'I asked for privacy. They gave me charts. Honestly? Great charts.',
			name: 'Pickles',
			details: 'Dachshund, 7'
		},
		{
			breed: 'greyhound',
			quote: 'My human now knows I sleep 16 hours a day. I regret nothing.',
			name: 'Luna',
			details: 'Greyhound, 5'
		}
	] as const;
</script>

<section class="container">
	<p class="eyebrow">Reviewed by the customers who matter</p>
	<div class="grid">
		{#each reviews as review (review.name)}
			<figure>
				<DogAvatar breed={review.breed} label="{review.name}, a {review.details.split(',')[0]}" />
				<blockquote>“{review.quote}”</blockquote>
				<figcaption>{review.name} — {review.details}</figcaption>
			</figure>
		{/each}
	</div>
</section>

<style>
	section {
		padding-block: 120px;
	}

	.eyebrow {
		margin-bottom: 48px;
	}

	.grid {
		display: flex;
		flex-wrap: wrap;
		gap: 48px;
	}

	figure {
		flex: 1 1 300px;
		display: flex;
		flex-direction: column;
		gap: 24px;
	}

	blockquote {
		font-family: var(--serif);
		font-style: italic;
		font-size: 32px;
		line-height: 1.15;
	}

	figcaption {
		margin-top: -4px;
		font-size: 15px;
		color: var(--muted);
	}
</style>
