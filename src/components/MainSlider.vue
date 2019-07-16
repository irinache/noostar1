<template>
	<div>
		<div class="container">
			<div class="row">
				<div id="right" class="arr" v-on:click = "right"></div>
				
				<div id="left" class="arr" v-on:click = "left"></div>
			</div>			
		</div>		
		<div id="slide" class="slider">
			<div class="slides">
				<div class="slide-single">				
				<div class="text">
					<h1>
						Учебный центр «Noostar» 1
					</h1>
					<p class="welcome_text">
						Учебный центр «Noostar»<br>
						Обучающие программы по программированию<br>
						и интернет-технологиям для людей любого<br>
						возраста и с любой базой знаний<br>						
					</p>
					<a href="#" class="orange_btn">Стать студентом</a>
				</div>
			</div>
			<div class="slide-single">				
				<div class="text">
					<h1>
						Учебный центр «Noostar» 2
					</h1>
					<p class="welcome_text">
						Учебный центр «Noostar»<br>
						Обучающие программы по программированию<br>
						и интернет-технологиям для людей любого<br>
						возраста и с любой базой знаний<br>						
					</p>
					<a href="#" class="orange_btn">Стать студентом</a>
				</div>
			</div>
			<div class="slide-single">				
				<div class="text">
					<h1>
						Учебный центр «Noostar» 3
					</h1>
					<p class="welcome_text">
						Учебный центр «Noostar»<br>
						Обучающие программы по программированию<br>
						и интернет-технологиям для людей любого<br>
						возраста и с любой базой знаний<br>						
					</p>
					<a href="#" class="orange_btn">Стать студентом</a>
				</div>
			</div>			
			</div>
			
		</div>
	</div>
	
</template>

<script>
	export default {
		data: function () {
			return{
				slider_wrapper: 0,
				l_arr: false,
				r_arr: true,
				cards: []
			}				
		},
		methods:{
			getNum: function(str){			
				return +str.replace(/[^\-\d]+/g, "");
			},
			getLeft: function(){
				return this.getNum(this.cards.style.left);
			},	
			getMax: function(){
				return Math.abs(this.cards.offsetWidth - this.offset);
			},
			switchArrows: function(arr){
				if (arr.classList.indexOf("active") != -1){
					arr.classList.remove("active")

				}
			},
			right: function(){
				if(!this.l_arr){
					document.getElementById('left').classList.add("active");
					document.getElementById('left').classList.remove("unactive");
					this.l_arr = true;		
				}
				if(Math.abs(this.getLeft()) + this.offset < this.getMax())
					this.cards.style.left = this.getLeft() - this.offset + 'px';			
				else if (Math.abs(this.getLeft()) + this.offset == this.getMax()){
					this.cards.style.left = this.getLeft() - this.offset + 'px';
					this.r_arr = false;	
					document.getElementById('right').classList.add("unactive");
					document.getElementById('right').classList.remove("active");
				}
				else{
					this.r_arr = false;	
					document.getElementById('right').classList.add("unactive");
					document.getElementById('right').classList.remove("active");
				}				
			},
			left: function(){
				if(!this.r_arr){
					document.getElementById('right').classList.add("active");
					document.getElementById('right').classList.remove("unactive");
					this.r_arr = true;		
				}
				if(this.getLeft() + this.offset < 0 )
					this.cards.style.left = this.getLeft() + this.offset + 'px';
				else if (this.getLeft() + this.offset == 0){
					this.cards.style.left = this.getLeft() + this.offset + 'px';
					this.l_arr = false;	
					document.getElementById('left').classList.add("unactive");
					document.getElementById('left').classList.remove("active");
				}
				else{
					this.l_arr = false;	
					document.getElementById('left').classList.add("unactive");
					document.getElementById('left').classList.remove("active");
				}
			},		
			handleResize: function(event){				
				console.log(" resize");
				let slides = document.querySelectorAll('.slide-single');

				this.cards = document.querySelector('.slides');
			
				this.card_width = document.querySelector('.slide-single').offsetWidth; 
				console.log(this.card_width)
				this.offset = this.card_width;
			
			
				this.cards.style.width = slides.length*this.offset + 'px';

				this.cards.style.left = 0;

				this.l_arr = false;	
				document.getElementById('left').classList.remove("active");
				document.getElementById('left').classList.add("unactive");

				this.r_arr = true;	
				document.getElementById('right').classList.remove("unactive");
				document.getElementById('right').classList.add("active");
			}			
		},
		mounted: function () {
		    let slides = document.querySelectorAll('.slide-single');

			this.cards = document.querySelector('.slides');
			//console.log(this.cards)
			this.card_width = document.querySelector('.slide-single').offsetWidth; 
			this.offset = this.card_width;
			
			
			this.cards.style.width = slides.length*this.offset + 'px';
			

			document.getElementById('left').classList.add("unactive");
			document.getElementById('right').classList.add("active");

			this.$nextTick(function() {
				window.addEventListener('resize', this.handleResize);
			});
			//console.log("pre resize");
			//this.handleResize();
		}
	
	}

</script>

<style>	
	.slider{
		font-size: 0; 
		overflow: hidden;
		width: 100%;
		margin: 0 auto;
		display: inline-block;
		vertical-align: middle;
		position: relative;
		height: 600px;		
	}

	.slides{
		
		position: absolute;	
		transition: all ease 1s;
		z-index: 10;
 		text-align: left;
 		top: 0;
 		left: 0;
	}
	.slide-single {
		width: 100vw;	
		height: 600px;
		transition: all ease 1s;
		display: inline-block;
		background: url('../assets/images/bg-header.jpg') no-repeat center top/cover
	}
	#right{		
		background: url("../assets/images/arrow_right_inactive.png") no-repeat center;
		right: 70px;
	}
	#left{		
		background: url("../assets/images/arrow_left_inactive.png") no-repeat center;
		left:  70px;
	}
	.arr{
		position: absolute;
		top: 350px;
		width: 86px;
		height: 86px;
		z-index: 13;
	}
	.text{
		margin: 180px 0 0 200px;
		z-index: 10;
		color: white;
		text-align: left;	
	}
	h1{
		font-family: Muller;
		font-weight: bold;
		font-size: 44px;
	}
	.welcome_text{
		font-family: Muller;
		font-size: 20px;
		margin-top: 36px;
		margin-bottom: 28px;
	}
	.orange_btn{
		background-color: #ff5215;
		color: white;
		font-family: Muller;
		font-weight: bold;
		font-size: 12px;
		border-radius: 5px;
		text-transform: uppercase;

		padding: 12px 25px 10px 25px;
		
	}
	a:hover{
		background-color: #ff652f;
		color: white;
		text-decoration: none;
	}


</style>