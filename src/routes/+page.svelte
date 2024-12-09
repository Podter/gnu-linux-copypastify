<script>
	import { useCompletion } from '@ai-sdk/svelte';
	import DicesIcon from 'lucide-svelte/icons/dices';
	import LoaderIcon from 'lucide-svelte/icons/loader';
	import SquarePenIcon from 'lucide-svelte/icons/square-pen';

	import { Button } from '$lib/components/ui/button';
	import { Input } from '$lib/components/ui/input';
	import { Textarea } from '$lib/components/ui/textarea';
	import { GNU_COPYPASTA, RANDOM_MESSAGES } from '$lib/constants';

	const { completion, input, handleSubmit, isLoading } = useCompletion();

	function randomize() {
		const text = RANDOM_MESSAGES[Math.floor(Math.random() * RANDOM_MESSAGES.length)];
		if ($input === text) {
			randomize();
		} else {
			$input = text;
		}
	}
</script>

<main
	class="mx-auto flex min-h-svh w-full max-w-4xl flex-col items-center justify-center space-y-6 p-6"
>
	<div class="space-y-3 text-center">
		<h1 class="text-2xl font-bold sm:text-3xl md:text-4xl">GNU/Linux Copypastify</h1>
		<p class="text-sm font-medium text-muted-foreground">
			Turn any debatable text into a GNU/Linux copypasta
		</p>
	</div>
	<form class="flex w-full max-w-sm flex-col items-center space-y-3" on:submit={handleSubmit}>
		<Input
			bind:value={$input}
			name="prompt"
			id="input"
			placeholder="Enter your text here"
			disabled={$isLoading}
		/>
		<div class="grid grid-cols-2 gap-2">
			<Button type="submit" disabled={$isLoading}>
				{#if $isLoading}
					<LoaderIcon size={16} class="mr-2 animate-spin" />
				{:else}
					<SquarePenIcon size={16} class="mr-2" />
				{/if}
				Generate
			</Button>
			<Button type="button" variant="secondary" disabled={$isLoading} onclick={randomize}>
				<DicesIcon size={16} class="mr-2" /> Randomize
			</Button>
		</div>
	</form>
	<Textarea
		value={$completion}
		readonly
		placeholder={$isLoading ? 'Generating...' : `${GNU_COPYPASTA.slice(0, 199)}...`}
		class="h-80"
	></Textarea>
</main>
