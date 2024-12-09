<script lang="ts">
	import Podter from '$lib/components/podter.svelte';
	import ThemeToggle from '$lib/components/theme-toggle.svelte';

	import '../app.css';

	import { ModeWatcher } from 'mode-watcher';

	let { children } = $props();
</script>

<ThemeToggle />

{@render children()}

<Podter />

<ModeWatcher />
