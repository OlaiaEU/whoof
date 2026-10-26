<svg
	viewBox="0 0 600 300"
	role="img"
	aria-label="Illustration of a greyhound curled up asleep, wearing a Whoof tag"
>
	<ellipse cx="300" cy="266" rx="250" ry="16" fill="rgba(34,32,28,0.07)" />
	<ellipse cx="335" cy="190" rx="190" ry="76" fill="#A7A39B" />
	<ellipse cx="455" cy="232" rx="72" ry="34" fill="#8E8A82" />
	<path
		d="M505 222 C566 250 526 282 420 272 C384 268 364 264 344 260"
		fill="none"
		stroke="#8E8A82"
		stroke-width="12"
		stroke-linecap="round"
	/>
	<rect x="56" y="240" width="200" height="22" rx="11" fill="#E6E1D7" />
	<ellipse cx="160" cy="205" rx="80" ry="52" fill="#A7A39B" />
	<ellipse cx="96" cy="222" rx="50" ry="26" fill="#A7A39B" />
	<path d="M120 172 L126 172 L104 238 L92 236 Z" fill="#E6E1D7" />
	<circle cx="50" cy="218" r="8" fill="#22201C" />
	<path d="M186 166 C212 148 236 158 230 182 C216 176 202 176 188 182 Z" fill="#7C7870" />
	<path d="M140 196 Q152 204 164 196" fill="none" stroke="#22201C" stroke-width="3" stroke-linecap="round" />
	<path d="M226 156 C246 174 248 228 232 250 L248 252 C264 228 262 170 242 152 Z" fill="#1F3A2E" />
	<rect x="240" y="230" width="22" height="22" rx="7" fill="#D6D3CC" stroke="#8E8B85" stroke-width="1" />
	<circle cx="256" cy="236" r="2" fill="#E3A33B" />
	<g class="zzz" font-family="Instrument Serif, serif" font-style="italic" fill="#6B6459">
		<text x="118" y="122" font-size="36">z</text>
		<text x="146" y="94" font-size="28">z</text>
		<text x="168" y="72" font-size="20">z</text>
	</g>
</svg>

<style>
	svg {
		display: block;
		width: 100%;
		height: auto;
	}

	.zzz text {
		animation: float 3s ease-in-out infinite;
	}

	.zzz text:nth-child(2) {
		animation-delay: 0.4s;
	}

	.zzz text:nth-child(3) {
		animation-delay: 0.8s;
	}

	@keyframes float {
		0%,
		100% {
			opacity: 0.35;
			transform: translateY(0);
		}
		50% {
			opacity: 1;
			transform: translateY(-6px);
		}
	}

	@media (prefers-reduced-motion: reduce) {
		.zzz text {
			animation: none;
		}
	}
</style>
