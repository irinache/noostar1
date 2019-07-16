<template>
	<a href="#" class="orange_btn">{{text}}</a>
</template>

<script>
	export default{
		props: {
			text: String,
		
		},
		mounted(){
			
		}
	}
</script>

<style>
	.orange_btn{
		background-color: #ff5215;
		color: white;
		font-family: Muller;
		font-weight: bold;
		font-size: 12px;
		border-radius: 5px;
		text-transform: uppercase;
		padding: 10px 25px 8px 25px;		
	}
	.orange_btn:hover{
		background-color: #ff652f;
		color: white;
		text-decoration: none;
	}
	@media (max-width: 482px) {   
		.orange_btn{
			display: block;
			width: 80%;
			margin: 10px auto 0 auto;
		}
	}
</style>