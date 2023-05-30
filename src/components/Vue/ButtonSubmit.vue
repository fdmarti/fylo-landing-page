<template>
	<button>{{ text }}</button>
</template>
<script setup>
	const { text } = defineProps(['text']);
</script>
<style>
	button {
		border: none;
		background-color: var(--BrightBlue);
		color: var(--LightGrayishBlue);
		font-family: var(--raleway);
		font-weight: 700;
		font-size: 17px;
		letter-spacing: 1px;
		border-radius: 5px;
		height: 53px;
		width: 250px;
	}
	button:hover {
		cursor: pointer;
		background-color: var(--BrightBlueHover);
	}

	@media (max-width: 991px) {
		button {
			width: 340px;
			max-width: 340px;
		}
	}
</style>
