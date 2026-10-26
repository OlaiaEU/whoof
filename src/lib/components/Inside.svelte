<script lang="ts">
	type Kind = 'shell' | 'antenna' | 'board' | 'battery' | 'sensor' | 'clip';

	type Layer = {
		kind: Kind;
		name: string;
		kicker: string;
		title: string;
		desc: string;
		spec: string;
	};

	// top of the stack first
	const layers: Layer[] = [
		{
			kind: 'shell',
			name: 'Shell',
			kicker: '01 / Shell',
			title: 'Chew-rated aluminium.',
			desc: 'Tested by forty Labradors. Survives sofa dives, puddles and the vacuum cleaner.',
			spec: '6061 aluminium · IP68'
		},
		{
			kind: 'antenna',
			name: 'Antenna',
			kicker: '02 / Antenna ring',
			title: 'GPS, LTE-M, Bluetooth.',
			desc: 'Powers Lost Dog Mode. Finds them past the fence, under the bed, or at the neighbour’s barbecue.',
			spec: 'Accurate to 3 m'
		},
		{
			kind: 'board',
			name: 'Wag Engine',
			kicker: '03 / Logic board',
			title: 'The Wag Engine.',
			desc: 'A 6-axis motion sensor and a tiny neural chip that can tell a zoomie from a sniff from a long stare at the postman.',
			spec: '6-axis IMU · on-device ML'
		},
		{
			kind: 'battery',
			name: 'Battery',
			kicker: '04 / Battery',
			title: 'Fourteen days.',
			desc: 'Charges on a bone-shaped dock in 90 minutes. Outlasts every toy you have ever bought them.',
			spec: '320 mAh Li-Po'
		},
		{
			kind: 'sensor',
			name: 'Biosensor',
			kicker: '05 / Sensor base',
			title: 'Reads through fur.',
			desc: 'Optical heart rate, breathing and temperature through up to 5 cm of fur. Fluffy dogs welcome.',
			spec: 'PPG · thermal · 25 Hz'
		},
		{
			kind: 'clip',
			name: 'Clip',
			kicker: '06 / Collar clip',
			title: 'Two-second clip.',
			desc: 'Fits any collar from 10 to 40 mm, and breaks away under strain so it never snags.',
			spec: 'Breakaway mount'
		}
	];

	const intro = {
		kicker: 'Inside the tag',
		title: 'Nine grams of very serious science.',
		desc: 'Keep scrolling. We’ll take it apart so you don’t have to.',
		spec: ''
	};

	const n = layers.length;
	const backToFront = layers.map((layer, i) => ({ layer, i })).reverse();

	let section: HTMLElement;
	let progress = $state(0);

	function update() {
		if (!section) return;
		const rect = section.getBoundingClientRect();
		const scrollable = rect.height - window.innerHeight;
		progress = scrollable > 0 ? Math.min(1, Math.max(0, -rect.top / scrollable)) : 0;
	}

	$effect(update);

	// first ~30% of the scroll pulls the stack apart, the rest walks through each layer in turn
	const spread = $derived.by(() => {
		const t = Math.min(1, progress / 0.3);
		return t * t * (3 - 2 * t);
	});
	const gap = $derived(8 + spread * 92);
	const active = $derived(
		progress < 0.32 ? -1 : Math.min(n - 1, Math.floor(((progress - 0.32) / 0.66) * n))
	);
	const current = $derived(active < 0 ? intro : layers[active]);

	function layerTransform(i: number) {
		const z = Math.round((n - 1 - i) * gap - ((n - 1) * gap) / 2);
		const x = i === active ? 56 : 0;
		return `translate3d(${x}px, 0, ${z}px)`;
	}

	function layerOpacity(i: number) {
		return active < 0 || i === active ? 1 : 0.28;
	}
</script>

<svelte:window onscroll={update} onresize={update} />

<section id="inside" bind:this={section}>
	<div class="sticky">
		<div class="container inner">
			<div class="copy">
				<p class="eyebrow kicker">{current.kicker}</p>
				<h2 class="display title">{current.title}</h2>
				<p class="desc">{current.desc}</p>
				<p class="spec">{current.spec}</p>
				<ol class="steps">
					{#each layers as layer, i (layer.kind)}
						<li class:done={active > i} class:active={active === i}>
							0{i + 1} — {layer.name}
						</li>
					{/each}
				</ol>
				<div class="progress"><div style:width="{progress * 100}%"></div></div>
			</div>

			<div class="stage" aria-hidden="true">
				<div class="shadow"></div>
				<div class="scaler">
					<div class="tag">
						{#each backToFront as { layer, i } (layer.kind)}
							<div
								class="layer layer-{layer.kind}"
								style:transform={layerTransform(i)}
								style:opacity={layerOpacity(i)}
							>
								{#if layer.kind === 'shell'}
									<span class="logo">W</span>
								{:else if layer.kind === 'board'}
									<span class="chip chip-lg"></span>
									<span class="chip chip-md"></span>
									<span class="pad pad-wide"></span>
									<span class="pad pad-round"></span>
								{:else if layer.kind === 'battery'}
									320 mAh
								{:else if layer.kind === 'sensor'}
									<span class="led led-green"></span>
									<span class="lens"></span>
									<span class="led led-red"></span>
								{:else if layer.kind === 'clip'}
									<span class="bar"></span>
								{/if}
							</div>
						{/each}
					</div>
				</div>
			</div>
		</div>
	</div>
</section>

<style>
	section {
		position: relative;
		height: 3400px;
		background: var(--pine);
		color: var(--linen);
	}

	.sticky {
		position: sticky;
		top: 0;
		height: 100vh;
		height: 100svh;
		overflow: hidden;
	}

	.inner {
		height: 100%;
		display: flex;
		flex-wrap: wrap;
		align-items: center;
		align-content: center;
		gap: 24px 64px;
	}

	.copy {
		flex: 1 1 380px;
		min-width: 0;
	}

	.kicker {
		margin-bottom: 16px;
		color: var(--accent);
	}

	.title {
		margin-bottom: 16px;
		font-size: clamp(40px, 5vw, 64px);
		min-height: 2em;
	}

	.desc {
		margin-bottom: 12px;
		font-size: 19px;
		color: var(--pine-soft);
		max-width: 460px;
		min-height: 5em;
	}

	.spec {
		margin-bottom: 32px;
		font-family: var(--mono);
		font-size: 14px;
		color: var(--pine-muted);
		min-height: 1.6em;
	}

	.steps {
		list-style: none;
		margin: 0;
		padding: 0;
		display: flex;
		flex-direction: column;
		gap: 6px;
		font-family: var(--mono);
		font-size: 13px;
		letter-spacing: 0.06em;
		text-transform: uppercase;
		color: #82998c;
	}

	.steps li {
		transition: color 0.3s ease;
	}

	.steps li.done {
		color: #e9e3d6;
	}

	.steps li.active {
		color: var(--accent);
	}

	.progress {
		margin-top: 32px;
		height: 2px;
		max-width: 460px;
		background: var(--pine-line);
	}

	.progress div {
		height: 2px;
		background: var(--accent);
	}

	.stage {
		flex: 1 1 440px;
		min-width: 0;
		height: 600px;
		display: flex;
		align-items: center;
		justify-content: center;
		perspective: 1600px;
		position: relative;
	}

	.shadow {
		position: absolute;
		bottom: 40px;
		width: 360px;
		max-width: 90%;
		height: 90px;
		border-radius: 50%;
		background: radial-gradient(ellipse, rgba(8, 20, 14, 0.85), rgba(8, 20, 14, 0) 70%);
	}

	.scaler {
		transform-style: preserve-3d;
	}

	.tag {
		position: relative;
		width: 240px;
		height: 240px;
		transform-style: preserve-3d;
		transform: rotateX(58deg) rotateZ(-40deg);
	}

	.layer {
		position: absolute;
		inset: 0;
		transition:
			transform 0.15s linear,
			opacity 0.35s ease;
	}

	.layer-shell {
		border-radius: 72px;
		background: linear-gradient(140deg, #e6e3dc 0%, #b5b2ab 45%, #7d7a74 100%);
		border: 1px solid #f2f0ea;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.logo {
		font-family: var(--serif);
		font-size: 64px;
		color: rgba(40, 40, 38, 0.5);
	}

	.layer-antenna {
		border-radius: 72px;
		border: 12px solid #b87333;
	}

	.layer-board {
		inset: 10px;
		border-radius: 62px;
		background: #0f241b;
		border: 1px solid #3e6b57;
		display: flex;
		flex-wrap: wrap;
		align-items: center;
		justify-content: center;
		gap: 14px;
		padding: 40px;
	}

	.chip {
		background: #0b0b0a;
		border: 1px solid #c9a646;
	}

	.chip-lg {
		width: 70px;
		height: 70px;
		border-radius: 6px;
	}

	.chip-md {
		width: 44px;
		height: 44px;
		border-radius: 4px;
	}

	.pad {
		background: #c9a646;
	}

	.pad-wide {
		width: 30px;
		height: 18px;
		border-radius: 3px;
	}

	.pad-round {
		width: 18px;
		height: 18px;
		border-radius: 50%;
	}

	.layer-battery {
		inset: 22px;
		border-radius: 56px;
		background: #2b2b28;
		border: 1px solid #55544e;
		display: flex;
		align-items: center;
		justify-content: center;
		font-family: var(--mono);
		font-size: 14px;
		color: #a29e95;
	}

	.layer-sensor {
		border-radius: 72px;
		background: #161614;
		border: 1px solid #4a4944;
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 18px;
	}

	.led {
		width: 22px;
		height: 22px;
		border-radius: 50%;
	}

	.led-green {
		background: var(--accent);
		box-shadow: 0 0 24px var(--accent);
	}

	.led-red {
		background: #ff5a4e;
		box-shadow: 0 0 24px #ff5a4e;
	}

	.lens {
		width: 34px;
		height: 34px;
		border-radius: 50%;
		background: #0a0a09;
		border: 2px solid #5a5953;
	}

	.layer-clip {
		display: flex;
		align-items: center;
	}

	.bar {
		width: 100%;
		height: 72px;
		border-radius: 18px;
		background: #2a2a27;
		border: 1px solid #4a4944;
	}

	@media (max-width: 860px) {
		.inner {
			flex-direction: column;
			flex-wrap: nowrap;
			justify-content: center;
			gap: 8px;
		}

		.copy {
			flex: 0 0 auto;
			width: 100%;
		}

		.title {
			font-size: 34px;
		}

		.desc {
			font-size: 16px;
			min-height: 4.8em;
		}

		.steps {
			display: none;
		}

		.spec {
			margin-bottom: 12px;
		}

		.progress {
			margin-top: 0;
		}

		.stage {
			flex: 0 0 auto;
			width: 100%;
			height: 400px;
		}

		.shadow {
			bottom: 20px;
			height: 60px;
		}

		.scaler {
			transform: scale(0.55);
		}
	}

	@media (prefers-reduced-motion: reduce) {
		.layer,
		.steps li {
			transition: none;
		}
	}
</style>
