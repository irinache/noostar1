<template>
	<div class="teacher-card">		
		<div class="teacher-image">			
		</div>		
		<div class="teacher-info">
			<p class="teacher-name">
				{{name}}
			</p>
			<p class="teacher-specialty">
				{{specialty}}
			</p>
			<p class="teacher-text">
				{{info}}
			</p>		
			<div class="social-networks">
				<a href="#" class="viber m_btn"></a>
				<a href="#" class="telegram m_btn"></a>
				<a href="#"class="skype m_btn"></a>
			</div>
		</div>
	</div>
</template>

<script>
	export default {		
		data(){
			return{
				name: 'Иван Иванов',
				specialty: 'Тестировщик ПО',
				info: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit'
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
	.teacher-card{
		height: 455px;
		width: 310px;
		margin: 15px;
		border: 1px solid #d2d1d1;
		border-radius: 3px;
		display: inline-block;
		background-color: white;
	}
	.teacher-image{
		width: 100%;
		height: 200px;
		background: url("../assets/images/teacher.jpg") center top / cover;
		border-radius: 3px 3px 0px 0px;
		
	}
	.teacher-name{
		font-family: Muller Medium;
		color: #555555;
		font-size: 18px;
		margin-top: 30px;
	}
	.teacher-specialty{
		font-family: Muller UltraLight;
		color: #848383;
		font-size: 11px;
		margin-top: 14px;
		text-transform: uppercase;
	}
	.teacher-text{
		font-family: Muller Light;
		color: #848383;
		font-size: 12px;
		margin-top: 24px;
		width: 70%;
		margin: 24px auto 28px auto;
	}
	.m_btn{		
		height: 30px;
		width: 30px;
		display: inline-block;
		
		
	}
	.m_btn:hover{
		background-color: #e1e1ee;
	}
	.viber{		
		background: url("../assets/images/viber.png")  no-repeat center center / 70%;
		background-color: #e9e9f2;
	}
	.telegram{
		background: url("../assets/images/telegram.png")  no-repeat center center / 70%;
		background-color: #e9e9f2;
	}
	.skype{
		background: url("../assets/images/skype.png")  no-repeat center center / 70%;
		background-color: #e9e9f2;
	}
	@media (max-width: 482px) {   
		.teacher-card{
			width: 250px;

		}
	}
</style>