<template>
	<div>
		<slot></slot>
	</div>
</template>

<script>
	export default {

	}
</script>

<style scoped>
	div {
		width: 65px;
		height: 65px;
		line-height: 65px;
		border-radius: 50%;
		background-color: #FCB31B;
		color: #0C0C0C;
		display: flex;
		justify-content: center;
		font-size: 22px;
		font-weight: 600;
		cursor: pointer;
		box-shadow: 5px 5px 8px 0px rgba(34, 60, 80, 0.2), -2px -2px 5px 0px rgba(254, 243, 214, 0.2);
	}

	div:hover {
		box-shadow: 4px 4px 10px 1px rgba(34, 60, 80, 0.2) inset;
	}
</style>