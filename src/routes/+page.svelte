<script>
	import { HeroTypewriter } from '$lib';

	import { clsx } from 'clsx';

	let shown = false;

	function handleHeroComplete() {
		shown = true;
	}
</script>

<div class="mt-40 mx-auto text-center">
	<HeroTypewriter onComplete={handleHeroComplete} />
	<div
		class="md:mt-40 mt-20 flex md:flex-row flex-col text-white md:gap-40 gap-20 text-2xl justify-center"
	>
		<a
			href="/about"
			class={clsx(
				'transition-[opacity,transform] ease-in duration-300 hover:text-green-400',
				!shown && 'opacity-0 md:translate-y-5 pointer-events-none'
			)}>about me</a
		>
		<a
			href="/resume"
			class={clsx(
				'transition-[opacity,transform] ease-in duration-300 delay-300 hover:text-green-400',
				!shown && 'opacity-0 md:translate-y-5 pointer-events-none'
			)}>resume</a
		>
		<a
			href="/projects"
			class={clsx(
				'transition-[opacity,transform] ease-in duration-300 delay-[600ms] hover:text-green-400',
				!shown && 'opacity-0 md:translate-y-5 pointer-events-none'
			)}>projects</a
		>
	</div>
</div>

<style lang="postcss">
	:global(html) {
		background-color: theme(colors.black);
	}
</style>
