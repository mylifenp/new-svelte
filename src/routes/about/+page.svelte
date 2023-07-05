<script lang="ts">
	export let increase_disabled = false;
	export let decrease_disabled = false;
	let x = 0;
	let y = 0;

	function yPlusAValue(value: number) {
		const total = y + value;
		if (total <= 0) {
			decrease_disabled = true;
			return 0;
		} else if (total >= 10) {
			increase_disabled = true;
			return 10;
		} else {
			increase_disabled = false;
			decrease_disabled = false;
			return y + value;
		}
	}
	$: total = yPlusAValue(x);
</script>

<div class="flex flex-col justify-between m-8 items-center">
	<div class="text-9xl text-cyan-400 m-12 whitespace-nowrap">Total: {total}</div>

	<div>
		<button
			disabled={increase_disabled}
			class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded {increase_disabled
				? 'opacity-50 cursor-not-allowed'
				: ''}"
			on:click={() => x++}>Increase X</button
		>
		<button
			disabled={decrease_disabled}
			class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded {decrease_disabled
				? 'opacity-50 cursor-not-allowed'
				: ''}"
			on:click={() => x--}>Decrease X</button
		>
	</div>
	<pre class="info">{increase_disabled ? 'max value 10 reached.' : ''}</pre>
	<pre class="info">{decrease_disabled ? 'min value 0 reached.' : ''}</pre>
</div>

<style lang="postcss">
	.info {
		color: red;
		margin: 0.2rem;
		font-size: x-small;
	}
</style>
