<script lang="ts">
	import '../app.postcss';
	import { AppShell, AppBar, AppRail, AppRailAnchor, AppRailTile } from '@skeletonlabs/skeleton';

	import thunderStoreLogo from '$lib/images/thunderstore-logomark-white.svg';

	// Highlight JS
	import hljs from 'highlight.js/lib/core';
	import 'highlight.js/styles/github-dark.css';
	import { storeHighlightJs } from '@skeletonlabs/skeleton';
	import xml from 'highlight.js/lib/languages/xml'; // for HTML
	import css from 'highlight.js/lib/languages/css';
	import javascript from 'highlight.js/lib/languages/javascript';
	import typescript from 'highlight.js/lib/languages/typescript';

	hljs.registerLanguage('xml', xml); // for HTML
	hljs.registerLanguage('css', css);
	hljs.registerLanguage('javascript', javascript);
	hljs.registerLanguage('typescript', typescript);
	storeHighlightJs.set(hljs);

	// Floating UI for Popups
	import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';
	import { storePopup } from '@skeletonlabs/skeleton';
	import { HomeFillBuildings } from 'svelte-remix';
	storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });

	let currentTile: number = 0;
</script>

<!-- App Shell -->
<AppShell>
	<svelte:fragment slot="header">
		<!-- App Bar -->
		<AppBar>
			<svelte:fragment slot="lead">
				<strong class="text-xl uppercase">Lodington.dev</strong>
			</svelte:fragment>
			<svelte:fragment slot="trail">
				<a
					class="btn btn-sm variant-ghost-surface"
					href="https://discord.gg/saKeaFZzum"
					target="_blank"
					rel="noreferrer"
				>
					Discord
				</a>
				<a
					class="btn btn-sm variant-ghost-surface"
					href="https://github.com/lodington"
					target="_blank"
					rel="noreferrer"
				>
					GitHub
				</a>
			</svelte:fragment>
		</AppBar>
	</svelte:fragment>
	<svelte:fragment slot="sidebarLeft">
		<AppRail>
			<!-- --- -->
			<AppRailTile bind:group={currentTile} name="tile-1" value={0} title="tile-1">
				<svelte:fragment slot="lead">
					<div class="flex justify-center items-center">
						<HomeFillBuildings class="fill-white" />
					</div>
				</svelte:fragment>
				<span>Home</span>
			</AppRailTile>
			<!-- --- -->
			<svelte:fragment slot="trail">
				<AppRailAnchor
					href="https://thunderstore.io/package/Lodington/?q=&ordering=last-updated&section=mods&nsfw=on&deprecated=on"
					target="_blank"
					title="ThunderStoreLink"
					class="w-16 h-16"
					><img alt="thunderstorelogo" class="m-5" src={thunderStoreLogo} /></AppRailAnchor
				>
			</svelte:fragment>
		</AppRail>
	</svelte:fragment>
	<!-- Page Route Content -->
	<slot />
</AppShell>
