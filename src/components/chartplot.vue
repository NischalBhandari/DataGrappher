<template>
	<div>
		<button v-on:click="addToValues(datas)" >Graph</button>
		<div class="small">
					<LineChart :chart-data="datacollection"></LineChart>
		</div>

<!-- 		<button @click = "fillData()">Randomize</button> -->
		
	</div>
</template>
<script>
	import LineChart from './LineChart.js'
	export default{
		name:"ChartPlot",
		props: ["datas"],
		components:{
			LineChart
		},
		data(){
			return{
				value: [],
				dates: [],
				datacollection: null
			}
		},

		methods:{
			addToValues(datas){
				var x = []
				var y = []
				var data;
				var eta;
				for(data in datas){
					console.log(datas[data].Closing_Price)
					x.push(datas[data].Closing_Price)
					y.push(datas[data].Date_Time)
			}
				console.log("this is the array ",x)
				console.log("this is the datetime", y)
				this.value=x
				this.dates = y
				this.fillData()

			},
			fillData () {
       this.datacollection = {
          labels: this.dates,
        datasets: [
            {
              label: "company",
              backgroundColor: '#f87979',
              data:this.value
/*              data: [this.getRandomInt(), this.getRandomInt()]*/
            }
          ]
        }
      },
      getRandomInt () {
        return Math.floor(Math.random() * (50 - 5 + 1)) + 5
      }
    },




		mounted(){
			this.fillData()
		},
}
	
</script>
<style scoped>
.small {
    max-width: 500px;
    margin:  150px auto;
  }
</style>