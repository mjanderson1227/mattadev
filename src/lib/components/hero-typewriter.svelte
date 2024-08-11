<script lang="ts">
	import { quartIn as easing } from 'svelte/easing';
	import { tweened, type Tweened } from 'svelte/motion';

	interface HeroTypewriterProps {
		onComplete?: () => void;
	}

	let { onComplete }: HeroTypewriterProps = $props();

	const text = 'Matthew Anderson';
	let progress = $state(0);
	let done = $state(false);
	let progressStore: Tweened<number>;

	$effect(() => {
		progressStore = tweened(0, {
			duration: 1500,
			easing
		});

		progressStore.set(text.length);

		return progressStore.subscribe((val) => (progress = val));
	});

	$effect(() => {
		if (progress >= text.length) {
			if (onComplete) onComplete();
			done = true;
		}
	});
</script>

<h1 class="md:text-6xl sm:text-5xl text-4xl font-bold text-gray-200">
	{text.substring(0, progress)}
	{#if !done}
		<span class="transition-[height] duration-500 w-1 h-10 bg-gray-200 text-black inline-block"
		></span>
	{/if}
</h1>

<style lang="postcss">
</style>
