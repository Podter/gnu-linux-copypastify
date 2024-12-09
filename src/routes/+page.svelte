<script>
	import { useCompletion } from '@ai-sdk/svelte';

	const { completion, input, handleSubmit } = useCompletion();
</script>

<form on:submit={handleSubmit}>
	<input name="prompt" bind:value={$input} id="input" class="input" />
	<button type="submit" class="btn">Submit</button>
</form>
<textarea value={$completion} readonly class="textarea"></textarea>
