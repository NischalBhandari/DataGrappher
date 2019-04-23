<template>
	<div>
		<form @submit="startsearch">
		<input type="text"  v-model="company" name="company" placeholder="search company ... ">
		<input type="submit" name="Submit">
	</form>

	</div>
</template>



<script>
	import axios from 'axios';
export default{

	name: "searching",
	data(){
		return{
			company: '',
			values:[]

		}
	},
	methods:{
		startsearch(e){
        let url='http://192.168.2.103:5000/jsonshow/'+ this.company
		e.preventDefault();
        axios.get(url)
		.then((res)=> {this.values = res.data
            this.$emit('foundthis',this.values)});
/*
        const transmit=JSON.parse(JSON.stringify(this.values));
        console.log(transmit)*/
            

	}

	},


}	
</script>

<style scoped >
	

</style>