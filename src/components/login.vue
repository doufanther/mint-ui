<template>
	<div>
		<p>
			<input v-model="name" />
		</p>
		<p>
			<input v-model="word" />
		</p>
		<p @click="login">登录</p>
	
	</div>
</template>

<script>
	import axios from 'axios'
	export default {
		components: {
		   
		},
	    props: {
		    
		},
		data() {
		    return {
		    	name:'',
		    	word:''
			}
		},
		created(){
			
		},
		computed: {
		   
		},
		methods: {
			login(){
				axios.get('http://localhost:3000/product/2')
				  .then(function (response) {
				    console.log(response);
				  })
				  .catch(function (response) {
				    console.log(response);
				});
				//this.$router.push({ path: '/home' })
			}
		}
	}
</script>


<style scoped >
	
</style>