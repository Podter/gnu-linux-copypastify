<script>
	import { useCompletion } from '@ai-sdk/svelte';
	import DicesIcon from 'lucide-svelte/icons/dices';
	import SquarePenIcon from 'lucide-svelte/icons/square-pen';

	import { Button } from '$lib/components/ui/button';
	import { Input } from '$lib/components/ui/input';
	import { Textarea } from '$lib/components/ui/textarea';
	import { GNU_COPYPASTA } from '$lib/constants';

	const { completion, input, handleSubmit } = useCompletion();
</script>

<main
	class="mx-auto flex min-h-svh w-full max-w-4xl flex-col items-center justify-center space-y-6 p-6"
>
	<div class="space-y-3 text-center">
		<h1 class="text-2xl font-bold sm:text-3xl md:text-4xl">GNU/Linux Copypastify</h1>
		<p class="text-sm font-medium text-muted-foreground">
			Convert any text into GNU/Linux copypasta
		</p>
	</div>
	<form class="flex w-full max-w-sm flex-col items-center space-y-3" on:submit={handleSubmit}>
		<Input bind:value={$input} name="prompt" id="input" placeholder="Enter your text here" />
		<div class="grid grid-cols-2 gap-2">
			<Button type="submit">
				<SquarePenIcon size={16} class="mr-2" /> Generate
			</Button>
			<Button type="button" variant="secondary">
				<DicesIcon size={16} class="mr-2" /> Randomize
			</Button>
		</div>
	</form>
	<Textarea
		value={$completion}
		readonly
		placeholder={`${GNU_COPYPASTA.slice(0, 199)}...`}
		class="h-80"
	></Textarea>
</main>
