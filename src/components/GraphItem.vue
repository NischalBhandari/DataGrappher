<template>
	<div class="todo-item">
<!-- 		this is done to compute the rising of falling of the data 
 -->		
 		{{showRising()}}
		<div v-bind:class="{'is-complete':datas.rising}">
		<p>
		{{datas.Traded_Companies}}
		<strong>On </strong>
		{{datas.Date_Time}}
		
	</p>
	<p> (No of Traded Shares / No of Transactions) <input type="checkbox" v-on:change="showdatas" > : {{Traded_SharestoNo_Of_Transactions}} </p>
	</div>
</div>
</template>
<script>
	export default{
	name: "GraphItem",
	props: ["datas"],
	data () {
		return {
		Traded_SharestoNo_Of_Transactions : ''
	}
	},
	methods: {

		showRising(){
			if(this.datas.Closing_Price - this.datas.Previous_Closing <= 0)
			{	console.log(this.datas.Previous_Closing)
				this.datas.rising = true
			}
			else{
				
			this.datas.rising = false
			}
		},
		showdatas(){

			console.log(this.datas.Traded_Shares)
			console.log(this.datas.No_Of_Transaction)
			this.Traded_SharestoNo_Of_Transactions = this.datas.Traded_Shares/this.datas.No_Of_Transaction;


		},
		jest(){
			
		}

	},
	created(){
		this.showRising()
	}
}
</script>

<style scoped>
	.todo-item {
	max-width: 500px;
	background: #f4f4f4;
	padding: 10px ;
	border-bottom: 1px #ccc dotted;
	color: red;
}
.is-complete{

/*	text-decoration: line-through;*/
/*	text-decoration-color: red;*/
	color: green;
	

}
.del{
	background: #ff0000;
	color: #fff;
	border: none;
	padding: 5px 9px;
	border-radius: 50%;
	cursor: pointer;
	float: right ;
}

</style>