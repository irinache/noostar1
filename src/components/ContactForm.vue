<template>
	<div class="grey_bg">	
		<div class="container justify-content-center">
			<div class="row col-md-12 m-0">
				<HeadingRight text="Есть вопросы? Напишите нам"/>		
			</div>
			<form>
				<div class="row m-0">
					<div class="col-md-6">
						<div class="form__group">
					        <label class="contact__label">Имя:</label>
					        <input class="contact__input" v-model="name" type="text" id="name">
					    </div>
					    <div class="form__group">
					        <label class="contact__label">Телефон:</label>
					        <input class="contact__input" v-model="phone" type="text" id="phone">
					    </div>
					</div>
					<div class="col-md-6">
					    <div class="form__group">
					        <label class="contact__label">Сообщение:</label>
					        <textarea class="contact__input message" v-model="message" id="message"></textarea> 
					    </div>
					</div>	
				</div>
				<div class="row m-0">
					<div class="col-md-12">
						<input type="submit" value="Отправить заявку" class="orange_btn float-right contact__btn">	
					</div>					
				</div>	    
			    
			</form>

		</div>
	</div>
	
</template>

<script>
	import HeadingRight from './HeadingRight.vue'
	import OrangeButton from './OrangeButton.vue'
	export default {
 		components: {
	  		HeadingRight,
	  		OrangeButton
  		},
  		data: function(){
  			return {
  				name: "",
  				phone: "",
  				message: ""
  			}
  		}  		
  	}
</script>

<style>
	input{		
		border: none;
	}
	textarea{
		 resize: none; 

	}
	.contact__label{
		display: block;
		text-align: left;
	}
	.contact__input{
		width: 100%;
		border: 1px solid #c9c9c9; 
		border-radius: 3px;
		font-family: Muller;
		font-style: 14px;
		padding-left: 7px;
	}
	.form__group{
		margin-bottom: 16px;
	}
	.message{
		height: 95px;
	}
	.contact__btn{		
		margin-top: 15px;
		margin-bottom: 80px;
	}
	label{
		font-family: Muller;
		font-size: 12px;
		margin-bottom: 5px;
		color: #848383;
	}
</style>