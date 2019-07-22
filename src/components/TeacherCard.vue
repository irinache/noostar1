<template>
	<div class="teacher-card">		
		<div class="teacher-card__image">			
		</div>		
		<div class="teacher-card__info">
			<p class="teacher-card__name">
				{{name}}
			</p>
			<p class="teacher-card__specialty">
				{{specialty}}
			</p>
			<p class="teacher-card__text">
				{{info}}
			</p>		
			<div class="teacher-card__social-networks">
				<a href="#" class="teacher-card__viber teacher-card__sn-btn"></a>
				<a href="#" class="teacher-card__telegram teacher-card__sn-btn"></a>
				<a href="#"class="teacher-card__skype teacher-card__sn-btn"></a>
			</div>
		</div>
	</div>
</template>

<script>
	export default {		
		props:{			
			name: String,
			specialty: String,
			info: String			
		}		
	}
</script>

<style lang="less">
	.teacher-card{
		height: 455px;
		width: 310px;
		margin: 15px;
		border: 1px solid #d2d1d1;
		border-radius: 3px;
		display: inline-block;
		background-color: white;
		& > p{
			margin: 0;
			padding: 0;
		}
		&__image{
			width: 100%;
			height: 200px;
			background: url("../assets/images/teacher.jpg") center top / cover;
			border-radius: 3px 3px 0px 0px;			
		}
		&__name{
			font-family: Muller Medium;
			color: #555555;
			font-size: 18px;
			margin-top: 30px;
		}
		&__specialty{
			font-family: Muller UltraLight;
			color: #848383;
			font-size: 11px;
			margin-top: 14px;
			text-transform: uppercase;
		}
		&__text{
			font-family: Muller Light;
			color: #848383;
			font-size: 12px;
			margin-top: 24px;
			width: 70%;
			margin: 24px auto 28px auto;
		}
		&__viber{		
			background: url("../assets/images/viber.png")  no-repeat center center / 70%;
			background-color: #e9e9f2;
		}
		&__telegram{
			background: url("../assets/images/telegram.png")  no-repeat center center / 70%;
			background-color: #e9e9f2;
		}
		&__skype{
			background: url("../assets/images/skype.png")  no-repeat center center / 70%;
			background-color: #e9e9f2;
		}
		&__sn-btn{
			height: 30px;
			width: 30px;
			margin: 3px;
			display: inline-block;
		}
		&__sn-btn:hover{
			background-color: #e1e1ee;
		}
	}	
	
	@media (max-width: 482px) {   
		.teacher-card{
			width: 250px;

		}
	}

	@media (max-width: 340px) {   
		.teacher-card{
			width: 220px;
			height: 400px;	
			&__image{				
				height: 150px;						
			}		
		}	
					
	}
</style>