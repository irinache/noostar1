<template>
	<div class="course-card" id="course-card">
		<div class="course-card__head">
			<div class="course-card__head-text">
				Начало обучения:
				<span class="course-card__date">
				{{date}}
				</span>
				<a class="orange_btn course-card__btn-pos">Идет набор</a>			
			</div>			
		</div>
		<div class="course-card__image">			
		</div>		
		<div class="course-card__course-info">
			<p class="course-card__info-title">
				Курс:
			</p>
			<div class="course-card__course-name">
				{{course_name}}
			</div>
			<div class="clearfix">
				<div class="course-card__duration">
					<p class="course-card__info-title">
						Длительность:
					</p>
					<p class="course-card__info-text">
						{{duration}}
					</p>
				</div>
				<div class="course-card__price">
					<p class="course-card__info-title">
						Цена обучения:
					</p>
					<p class="course-card__info-text">
						{{price}}
					</p>
				</div>
			</div>
			
			<div class="course-card__teacher">
				<p class="course-card__info-title">
					Преподаватель:
				</p>
				<p class="course-card__info-text">
					{{teacher}}
				</p>
			</div>
			<div class="course-card__info-btn">
				<a class="orange_btn course-card__btn-pos">Записаться на курс</a>
				
			</div>
			
		</div>
	</div>
</template>

<script>
	export default {
		props:{			
			date: String,
			course_name: String,
			duration: String,
			price: String,
			teacher: String
		},
		data(){
			return{				
			}
		}		
	}
</script>

<style lang="less">
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
		&__head-text{
			margin: 0 auto;
			margin-top: 20px;
		}	
		&__head{
			background-color: #0a063c;
			border-radius: 3px;
			font-family: Muller;
			font-size: 10px;
			text-align: center;
			color: white;
			height: 58px;
			overflow: auto;
		}
		&__date{
			font-family: Muller;
			font-weight: bold;
			font-size: 10px;
			color: white;
			margin-right: 5px;
		}
		&__image{
			width: 100%;
			height: 145px;
			background: url("../assets/images/course_img.jpg");
			margin-top: -3px;
		}
		&__course-name{
			font-family: Muller;
			font-weight: bold;
			color: #ff5215;
			text-transform: uppercase;
			font-size: 12px;
			text-align: left;		
			margin-left: 23px;		 
			margin-bottom: 13px;
			height: 35px;
		}
		&__info-title{
			margin-left: 23px;
			margin-top: 10px;
			margin-bottom: 3px;
			font-family: Muller;		
			font-size: 10px;
			color: #c7c7c7;
			text-align: left;
		}
		&__duration{
			float: left;
			width: 50%;
			border-top: 1px solid #d2d1d1;
			border-bottom:  1px solid #d2d1d1;
			
		}
		&__price{
			float: right;
			width: 50%;
			border-left: 1px solid #d2d1d1;
			border-top: 1px solid #d2d1d1;
			border-bottom:  1px solid #d2d1d1;
			
		}
		&__info-title{
			margin-left: 23px;
			margin-top: 10px;
			margin-bottom: 3px;
			font-family: Muller;		
			font-size: 10px;
			color: #c7c7c7;
			text-align: left;
		}
		&__info-text{
			margin-left: 23px;
			margin-bottom: 10px;
			font-family: Muller;		
			font-size: 10px;
			color: #676767;
			text-align: left;
		}
		&__teacher{
			border-bottom:  1px solid #d2d1d1;
		}
		&__info-btn{
			margin-top: 25px;
			text-align: center;
			margin-bottom: 10px;
			color: white;
		}
	}	
	
	.clearfix:after{
		content: ""; 
		display: table; 
		clear: both; 
	}
	

	@media (max-width: 482px) {   
		.course-card{
			width: 250px;
			height: 530px;
			&__btn-pos{
				width: 80%;
				display: block;
				margin: 10px auto 0 auto;
			}
			&__head{
				height: 100px;
			}
		}		
	}
	@media (max-width: 340px) {   
		.course-card{
			width: 220px;
			height: 550px;
			&__course-name{
				height: 50px;
			}
		}	
					
	}
</style>