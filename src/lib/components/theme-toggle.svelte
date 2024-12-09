<script lang="ts">
	import MoonIcon from 'lucide-svelte/icons/moon';
	import SunIcon from 'lucide-svelte/icons/sun';
	import { toggleMode } from 'mode-watcher';

	import { Button } from './ui/button';
</script>

<Button onclick={toggleMode} variant="outline" size="icon" class="absolute right-4 top-4">
	<SunIcon class="dark:hidden" size={16} />
	<MoonIcon class="hidden dark:block" size={16} />
	<span class="sr-only">Toggle theme</span>
</Button>
