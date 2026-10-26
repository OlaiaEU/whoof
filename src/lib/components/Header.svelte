<script lang="ts">
	const links = [
		{ href: '#inside', label: 'Inside' },
		{ href: '#features', label: 'Features' },
		{ href: '#app', label: 'App' },
		{ href: '#pricing', label: 'Pricing' }
	];
</script>

<header class="container">
	<a href="#top" class="logo">WHOOF</a>
	<nav aria-label="Main">
		{#each links as link (link.href)}
			<a href={link.href} class="link">{link.label}</a>
		{/each}
		<a href="#preorder" class="btn btn-pine cta">Pre-order</a>
	</nav>
</header>

<style>
	header {
		padding-block: 24px;
		display: flex;
		flex-wrap: wrap;
		align-items: center;
		justify-content: space-between;
		gap: 16px;
		border-bottom: 1px solid var(--line);
	}

	.logo {
		text-decoration: none;
		font-weight: 600;
		font-size: 18px;
		letter-spacing: 0.32em;
	}

	nav {
		display: flex;
		flex-wrap: wrap;
		align-items: center;
		gap: 8px 32px;
		font-size: 15px;
	}

	.link {
		text-decoration: none;
		color: var(--muted);
	}

	.link:hover {
		color: var(--ink);
	}

	.cta {
		min-height: 44px;
		padding: 0 20px;
	}
</style>
