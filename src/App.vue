<template>
	<div class="app">
		<output-area v-model:out=val v-model:history=historyMode></output-area>
		<input-area @addValueInOutputArea="checkValue"></input-area>
	</div>
</template>

<script>
	import OutputArea from "@/components/OutputArea"
	import InputArea from "@/components/InputArea"
	export default {
		components: {
			InputArea, OutputArea
		},
		data() {
			return {
				val: '',
				operationValue: undefined,
				firstValue: 0,
				historyMode: ''
			}
		},
		methods: {
			concatValAndStringValue(stringValue) {
				this.val += stringValue
			},
			performingOperations(firstVal, secondVal, operation) {
				switch(operation) {
					case "+":
						return String(+firstVal + +secondVal);
					case "-":
						return String(+firstVal - +secondVal);
					case "x":
						return String(+firstVal * +secondVal);
					case "/":
						return String(+firstVal / +secondVal);
					case "%":
						return String(+firstVal / 100 * +secondVal);
				}
			},
			determineTypeOperation(operation) {
				switch (operation) {
					case "+":
					case "-":
					case "x":
					case "/":
					case "%":
						this.firstValue = this.operationValue == undefined
							? this.firstValue = +this.firstValue + +this.val
							: this.firstValue = this.performingOperations(this.firstValue, this.val, this.operationValue);

						this.operationValue = operation;
						this.historyMode = this.historyMode + (this.val + this.operationValue);
						console.log(this.historyMode);
						this.val = "";
						break;
					case "+/-":
						if(this.val !== "") this.val = String(- +this.val);
						break;
					case "=":
						this.val = this.performingOperations(this.firstValue, this.val, this.operationValue);
						this.clear();
						break;
					case "<-":
						this.val = (this.val.length == 2 && this.val.slice(0, 1) == "-")
							? this.val = ""
							: this.val = this.val.slice(0, -1);
						break;
					case "AC":
						this.val = "";
						this.clear();
						break;
				}
			},
			clear() {
				this.firstValue = "0";
				this.operationValue = undefined;
				this.historyMode = "";
			},
			checkValue(value) {
				if(!isNaN(value) || (value === "." && this.val !== "")) {
					this.concatValAndStringValue(value)
				} else {
					this.determineTypeOperation(value)
				}
			}
		}
	}
</script>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Dosis:wght@200;300;400;500;600;700;800&display=swap');
	* {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}
	body {
		background-color: #FFF9E9;
		font-family: 'Dosis', sans-serif;
	}
	.app {
		width: 375px;
		margin: 25px auto;
		padding: 15px;
		background-color: #FCB31B;
		border-radius: 15px;
		box-shadow: 5px 5px 16px 3px rgba(34, 60, 80, 0.2);
	}
</style>