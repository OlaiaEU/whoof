<script lang="ts">
	type Breed = 'golden' | 'dachshund' | 'greyhound';

	let { breed, label, size = 96 }: { breed: Breed; label?: string; size?: number } = $props();
</script>

<svg
	viewBox="0 0 120 120"
	width={size}
	height={size}
	role={label ? 'img' : undefined}
	aria-label={label}
	aria-hidden={label ? undefined : 'true'}
>
	{#if breed === 'golden'}
		<circle cx="60" cy="60" r="60" fill="#E7D3B4" />
		<circle cx="60" cy="66" r="34" fill="#C98E4E" />
		<path d="M32 46 C18 52 16 90 28 96 C40 94 42 66 42 52 Z" fill="#A06A32" />
		<path d="M88 46 C102 52 104 90 92 96 C80 94 78 66 78 52 Z" fill="#A06A32" />
		<ellipse cx="60" cy="82" rx="17" ry="13" fill="#E9C48F" />
		<ellipse cx="60" cy="75" rx="6" ry="4.5" fill="#22201C" />
		<circle cx="48" cy="60" r="3" fill="#22201C" />
		<circle cx="72" cy="60" r="3" fill="#22201C" />
	{:else if breed === 'dachshund'}
		<circle cx="60" cy="60" r="60" fill="#EAD9C8" />
		<ellipse cx="60" cy="56" rx="26" ry="28" fill="#9C5530" />
		<ellipse cx="60" cy="84" rx="14" ry="22" fill="#9C5530" />
		<path d="M36 42 C20 48 18 96 32 104 C44 100 44 66 42 50 Z" fill="#6E3518" />
		<path d="M84 42 C100 48 102 96 88 104 C76 100 76 66 78 50 Z" fill="#6E3518" />
		<ellipse cx="60" cy="102" rx="6" ry="4.5" fill="#22201C" />
		<circle cx="50" cy="55" r="3" fill="#22201C" />
		<circle cx="70" cy="55" r="3" fill="#22201C" />
	{:else}
		<circle cx="60" cy="60" r="60" fill="#DCE3DA" />
		<ellipse cx="60" cy="56" rx="22" ry="26" fill="#A7A39B" />
		<path d="M48 68 L72 68 L66 106 Q60 110 54 106 Z" fill="#A7A39B" />
		<path d="M57 36 L63 36 L64 104 L56 104 Z" fill="#E6E1D7" />
		<path d="M40 40 C30 30 22 36 26 46 C32 46 38 46 42 48 Z" fill="#7C7870" />
		<path d="M80 40 C90 30 98 36 94 46 C88 46 82 46 78 48 Z" fill="#7C7870" />
		<ellipse cx="60" cy="106" rx="5" ry="4" fill="#22201C" />
		<circle cx="50" cy="54" r="2.8" fill="#22201C" />
		<circle cx="70" cy="54" r="2.8" fill="#22201C" />
	{/if}
</svg>

<style>
	svg {
		display: block;
		border-radius: 50%;
		flex: 0 0 auto;
	}
</style>
