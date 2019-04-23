<template>
<div>
	
	<div v-for="graph in graphdata">
			<GraphItem v-bind:datas="graph"/>
	</div>
	<ChartPlot v-bind:datas="graphdata" />
	
</div>

</template>

<script >
import GraphItem from './GraphItem.vue'	
import ChartPlot from './chartplot.vue'
export default {


	name: "graphworld",
	components: {
		GraphItem,
		ChartPlot
	},
	props: ["graphdata"]
}
</script>

<style scoped>
	h3{
		margin: 40px 0 0 ;
	}

</style>