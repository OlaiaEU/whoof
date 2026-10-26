<script lang="ts">
	import DogSitting from './dogs/DogSitting.svelte';
</script>

<section id="top" class="container hero">
	<div class="copy">
		<p class="eyebrow">Whoof Tag · Health tracker for dogs</p>
		<h1>The quantified <em>dog.</em></h1>
		<p class="lede">
			Sleep, activity, heart rate and the precise number of zoomies — measured on the collar,
			explained in plain English. Your dog won't notice. Your vet will.
		</p>
		<div class="actions">
			<a href="#preorder" class="btn btn-pine">Pre-order — €79</a>
			<a href="#inside" class="btn btn-outline">Look inside</a>
		</div>
	</div>

	<div class="visual">
		<div class="arch">
			<div class="sun"></div>
			<div class="dog"><DogSitting /></div>
			<div class="chip chip-heart">
				<p class="chip-label">Resting heart</p>
				<p class="chip-value">84 bpm</p>
			</div>
			<div class="chip chip-zoom">
				<p class="chip-label">Zoomies today</p>
				<p class="chip-value">3</p>
			</div>
		</div>
	</div>
</section>

<style>
	.hero {
		padding-block: 80px 112px;
		display: flex;
		flex-wrap: wrap;
		align-items: center;
		gap: 64px;
	}

	.copy {
		flex: 1 1 480px;
		min-width: 0;
	}

	.eyebrow {
		margin-bottom: 28px;
	}

	h1 {
		margin-bottom: 28px;
		font-family: var(--serif);
		font-weight: 400;
		font-size: clamp(56px, 8vw, 116px);
		line-height: 0.92;
		letter-spacing: -0.02em;
	}

	h1 em {
		color: var(--pine-text);
	}

	.lede {
		margin-bottom: 40px;
		font-size: 20px;
		max-width: 500px;
		color: var(--ink-2);
	}

	.actions {
		display: flex;
		flex-wrap: wrap;
		gap: 12px;
	}

	.visual {
		flex: 1 1 420px;
		min-width: 0;
		display: flex;
		justify-content: center;
	}

	.arch {
		position: relative;
		width: 420px;
		max-width: 100%;
		height: 540px;
		border-radius: 210px 210px 28px 28px;
		background: var(--camel);
		overflow: hidden;
		display: flex;
		align-items: flex-end;
		justify-content: center;
	}

	.sun {
		position: absolute;
		top: 72px;
		left: 50%;
		width: 220px;
		height: 220px;
		margin-left: -110px;
		border-radius: 50%;
		background: var(--accent);
		opacity: 0.55;
	}

	.dog {
		position: relative;
		width: 92%;
	}

	.chip {
		position: absolute;
		background: var(--paper);
		border-radius: 16px;
		padding: 12px 16px;
		box-shadow: 0 12px 30px rgba(34, 32, 28, 0.12);
	}

	.chip-heart {
		top: 140px;
		right: 18px;
	}

	.chip-zoom {
		bottom: 150px;
		left: 18px;
	}

	.chip-label {
		font-family: var(--mono);
		font-size: 11px;
		letter-spacing: 0.1em;
		text-transform: uppercase;
		color: var(--muted);
	}

	.chip-value {
		margin-top: 2px;
		font-size: 22px;
		font-weight: 500;
	}

	@media (max-width: 480px) {
		.arch {
			height: 460px;
		}
	}
</style>
