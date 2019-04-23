<template>
	<div class="calculator">
		<div class="display">{{current || '0'}}</div>
		<div class="btn" @click="clear">C</div>
		<div class="btn "@click="sign">+/-</div>
		<div class="btn" @click="percent">%</div>
		<div class="btn operator" @click="divide">/</div>
		<div class="btn" @click="append(7)">7</div>
		<div class="btn" @click="append(8)">8</div>
		<div class="btn" @click="append(9)">9</div>
		<div class="btn operator " @click="multiply">*</div>
		<div class="btn" @click="append(4)">4</div>
		<div class="btn" @click="append(5)">5</div>
		<div class="btn" @click="append(6)">6</div>
		<div class="btn operator" @click="substract">-</div>
		<div class="btn" @click="append(1)">1</div>
		<div class="btn" @click="append(2)">2</div>
		<div class="btn" @click="append(3)">3</div>
		<div class="btn operator" @click="sum">+</div>
		<div class="zero btn" @click="append(0)">0</div>
		<div class="btn" @click="dot">.</div>
		<div class="btn operator" @click="equal">=</div>
	</div>
</template>


<script>
	export default {
	name: "Calculator",
	data(){
		return {
			previous: null,
			current: '',
			operator: null,
			operatorClicked: false
		}
	},
	methods: {
		clear(){
			this.current=''
		},
		sign(){
			/*ternary operator to check if the string contains - then slice the 1st string else remove the */
			console.log(this.current.charAt(0))
/*			here slice(1) is used cause slice(0) just gives a copy of the string 
*/			this.current = this.current.charAt(0) === '-' ? 
			this.current.slice(1): `-${this.current}`;
			
		},
		percent(){
			this.current = `${parseFloat(this.current)/100}`
		},
		append(number){
			if(this.operatorClicked){
				this.current='';
				this.operatorClicked=false;
			}
			this.current = `${this.current}${number}`;
		},
		dot(){
			if(this.current.indexOf('.') === -1){
				this.append('.');
			}
		},
		setPrevious(){
			this.previous = this.current;
			this.operatorClicked = true;
		},
		divide(){
			this.operator = (a,b) => a/b;
			this.setPrevious()

		},
		multiply(){
			this.operator = (a,b) => a*b;
			this.setPrevious()
		},
		substract(){
			this.operator = (a,b) => a-b;
			this.setPrevious()
		},
		sum(){
			this.operator = (a,b) => a+b;
			this.setPrevious()			
		},
		equal(){
			this.current = `${this.operator(parseFloat(this.current), parseFloat(this.previous))}`;
			this.previous = null;
		}
	}
	
}
	
</script>

<style scoped>
	.calculator {
/*		to keep the whole calculator in center 
*/		margin: 0 auto;
		width: 200px;
		text-align: center;
		font-size: 40px;
		display: grid;
		grid-template-columns: repeat(4,1fr);
		grid-auto-rows: minmax(50px,auto);
		color: black;
	}
	.display {
		
		grid-column: 1 / 5 ;
		background-color : magenta;
		color: black;
	}
	.zero {
		
		grid-column: 1 / 3;
	}
	.btn {
		background-color: #eee;
		border: 1px solid #333;
		color: black;

	}
	.operator{
		background-color: orange;


	}
</style>