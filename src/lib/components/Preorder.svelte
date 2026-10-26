<script lang="ts">
	let email = $state('');
	let joined = $state(false);

	function join(event: SubmitEvent) {
		event.preventDefault();
		joined = true;
	}
</script>

<section id="preorder">
	<div class="container inner">
		<h2 class="display">Give your dog a reason <em>to be smug.</em></h2>
		{#if joined}
			<p class="sub" role="status">You're on the list. We'll be in touch before the treats run out.</p>
		{:else}
			<p class="sub">Join the waitlist for first dibs. Shipping this winter.</p>
			<form onsubmit={join}>
				<label for="email" class="visually-hidden">Email address</label>
				<input id="email" type="email" required placeholder="you@goodboy.dog" bind:value={email} />
				<button type="submit" class="btn btn-accent">Join the waitlist</button>
			</form>
		{/if}
	</div>
</section>

<style>
	section {
		background: var(--pine);
		color: var(--linen);
		padding-block: 140px;
	}

	.inner {
		max-width: 900px;
		text-align: center;
	}

	h2 {
		margin-bottom: 24px;
		font-size: clamp(48px, 7vw, 96px);
		line-height: 0.95;
	}

	h2 em {
		color: var(--accent);
	}

	.sub {
		margin-bottom: 44px;
		font-size: 19px;
		color: var(--pine-muted);
	}

	form {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		gap: 12px;
		max-width: 560px;
		margin: 0 auto;
	}

	input {
		flex: 1 1 260px;
		min-height: 54px;
		padding: 0 22px;
		border: 1px solid var(--linen);
		border-radius: 999px;
		background: var(--linen);
		color: var(--ink);
		font: inherit;
	}

	button {
		min-height: 54px;
	}
</style>
