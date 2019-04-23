<template>
	<div>
		<!-- submits the form data to addTodo method  -->
		<form @submit="addTodo">
			<!-- v-model provides a view default function to map the data to the data in the component 
			see in the AddTodo component where data is defined  -->
			<input type="text " v-model="title" name="title " placeholder="Add Todo...">
			<input type="submit" name="Submit">
		</form>
	</div>
</template>


<script >
	/*install uuid from npm */
	import uuid from 'uuid';
	export default {

		name: "AddTodo",
		data() {

			return {
				title: ''
			}
		},
		methods: {

			addTodo(e){
				/*e is the event of the model 
				e.preventDefault prevents the default behaviour of the form in sending it to the server */
				e.preventDefault();
				console.log(123);

				const newTodo={
					/*use uuid.v4 to create a unique id each time */
					id: uuid.v4(),
					title: this.title,
					completed: false
				}
				/*emits the add-todo event with a newTodo const data */
				this.$emit('add-todo', newTodo);
				/*clears the form*/ 
				this.title = '';
			}
		}
	}
</script>


<style scoped>
	form{

		display: flex;
	}
	input[type="text"]{
		flex: 10;
		padding: 5px;
	}
	input[type="submit"]{

		flex: 2;
	}
	

</style>