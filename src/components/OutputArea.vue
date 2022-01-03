<template>
	<div class="wrapper">
		<div class="history-mode">{{history}}</div>
		<div class="out-input">{{out}}</div>
	</div>
</template>

<script>
	export default {
		props: {
			out: {
				type: String,
				required: true
			},
			history: {
				type: String,
				required: true
			}
		}
	}
</script>

<style scoped>
	.wrapper {
		height: 150px;
		background-color: #FEF3D6;
		border-radius: 15px;
		box-shadow: 8px 8px 10px -5px rgba(34, 60, 80, 0.3) inset, 8px 8px 10px -5px rgba(34, 60, 80, 0.3);
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		align-items: flex-end;
	}
	div {
		font-size: 28px;
		font-weight: 600;
		padding: 5px 10px;
	}
	.history-mode {
		color: rgba(0, 0, 0, 0.3);
		font-size: 18px;
	}
</style>