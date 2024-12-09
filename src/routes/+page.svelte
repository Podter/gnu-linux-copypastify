<script>
	import { useCompletion } from '@ai-sdk/svelte';

	const { completion, input, handleSubmit } = useCompletion();
</script>

<form on:submit={handleSubmit}>
	<input name="prompt" bind:value={$input} id="input" />
	<button type="submit">Submit</button>
</form>
<textarea value={$completion} readonly></textarea>
