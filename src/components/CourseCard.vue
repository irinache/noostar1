<template>
	<div class="course-card" id="course-card">
		<div class="head">
			<div class="head-text">
				Начало обучения:
				<span class="date">
				{{date}}
				</span>

				<OrangeButton text = "Идет набор"/>
			</div>			
		</div>
		<div class="course-image">			
		</div>		
		<div class="course-info">
			<p class="info-title">
				Курс:
			</p>
			<div class="course-name">
				{{course_name}}
			</div>
			<div class="clearfix">
				<div class="duration">
					<p class="info-title">
						Длительность:
					</p>
					<p class="info-text">
						{{duration}}
					</p>
				</div>
				<div class="price">
					<p class="info-title">
						Цена обучения:
					</p>
					<p class="info-text">
						{{price}}
					</p>
				</div>
			</div>
			
			<div class="teacher">
				<p class="info-title">
					Преподаватель:
				</p>
				<p class="info-text">
					{{teacher}}
				</p>
			</div>
			<div class="info-btn">
				<OrangeButton text = "Записаться на курс"/>
			</div>
			
		</div>
	</div>
</template>

<script>
	import OrangeButton from './OrangeButton.vue'
	export default {
		components:{
			OrangeButton
		},
		props:{
			last: String,
			date: String,
			course_name: String,
			duration: String,
			price: String,
			teacher: String
		},
		data(){
			return{
				
			}
		},
		mounted(){
			//console.log(this.last);
			if (this.last == 'true'){
				document.querySelector(".course-card").style.margin = 0;
			}
		}
	}
</script>

<style>
	p{
		margin: 0;
		padding: 0;
	}
	.course-card{		
		height: 455px;
		width: 310px;
		margin: 15px;
		border: 1px solid #d2d1d1;
		border-radius: 3px;
		display: inline-block;
		background-color: white;	
	}
	.head{
		background-color: #0a063c;
		border-radius: 3px;
		font-family: Muller;
		font-size: 10px;
		text-align: center;
		color: white;
		height: 58px;
		overflow: auto;

	}
	.head-text{
		margin: 0 auto;
		margin-top: 20px;
	}
	.date{
		font-family: Muller;
		font-weight: bold;
		font-size: 10px;
		color: white;
		margin-right: 5px;		
	}
	.course-image{
		width: 100%;
		height: 145px;
		background: url("../assets/images/course_img.jpg");
		margin-top: -3px;
	}
	.course-name{
		font-family: Muller;
		font-weight: bold;
		color: #ff5215;
		text-transform: uppercase;
		font-size: 12px;
		text-align: left;
		height: 30px;
		margin-left: 23px;		 
		margin-bottom: 13px;
	}
	.duration{
		float: left;
		width: 50%;
		border-top: 1px solid #d2d1d1;
		border-bottom:  1px solid #d2d1d1;
		
	}
	.price{
		float: right;
		width: 50%;
		border-left: 1px solid #d2d1d1;
		border-top: 1px solid #d2d1d1;
		border-bottom:  1px solid #d2d1d1;
		
	}
	.info-title{
		margin-left: 23px;
		margin-top: 10px;
		margin-bottom: 3px;
		font-family: Muller;		
		font-size: 10px;
		color: #c7c7c7;
		text-align: left;
	}
	.info-text{
		margin-left: 23px;
		margin-bottom: 10px;
		font-family: Muller;		
		font-size: 10px;
		color: #676767;
		text-align: left;

	}
	.teacher{
		border-bottom:  1px solid #d2d1d1;
	}
	.clearfix:after{
		content: ""; 
		display: table; 
		clear: both; 
	}
	.info-btn{
		margin-top: 25px;
		text-align: center;
	}

	@media (max-width: 482px) {   
		.course-card{
			width: 250px;
			height: 500px;
		}
		.head{
			height: 100px;
		}
	}
</style>