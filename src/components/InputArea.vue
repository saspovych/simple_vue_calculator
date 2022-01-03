<template>
	<div class="wrapper">
		<my-button
			v-for="value in arrayInputValues"
			v-bind:val=value
			@click="clickOnInputButton(value)"
		>
			{{value}}
		</my-button>
	</div>
</template>

<script>
	import MyButton from "@/components/UI/MyButton"
	export default {
		components: {
			MyButton
		},
		data() {
			return {
				arrayInputValues : ["AC", "+/-", "%", "/",
												"7", "8", "9", "x",
												"4", "5", "6", "+",
												"1", "2", "3", "-",
												"0", ".", "<-", "=", ]
			}
		},
		methods: {
			clickOnInputButton(inputValue) {
				this.$emit("addValueInOutputArea", inputValue);
			}
		}
	}
</script>

<style scoped>
	.wrapper {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		grid-gap: 5px;
		padding: 15px 20px;
	}
</style>