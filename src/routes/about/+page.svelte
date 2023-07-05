<script lang="ts">
	let x = 0;
	let y = 0;

	function yPlusAValue(value: number) {
		return y + value;
	}
	$: total = yPlusAValue(x);
</script>

<div class="header">
	<div class="text-9xl text-cyan-400 m-12">Total: {total}</div>

	<div>
		<button
			class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
			on:click={() => x++}>Increment X</button
		>
		<button
			class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded"
			on:click={() => x--}>Decrease X</button
		>
	</div>
</div>

<style lang="postcss">
	.header {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		align-items: center;
		margin: 2rem;
	}
</style>
