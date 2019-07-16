<template>
	<div class="container-fluid">
		<div class="row">
			<Heading text = "Преподаватели" color="white"/>			
		</div>
		
		<div class="arr2 l2" v-on:click = "l">
				
		</div>
		<div class="slider3">
			<div class="teacher-cards" >
				<TeacherCard v-for="teacher in teachers"
				v-bind:key="teacher.name"
				v-bind:speciality="teacher.speciality" v-bind:info="teacher.info"
				/>		
			</div>	
		</div>
						
		<div class="arr2 r2" v-on:click = "r">
				
		</div>				
		
	</div>
</template>

<script>
	import Heading from './heading.vue'
	import TeacherCard from './TeacherCard.vue'
export default {
  components: {
  	Heading,
  	TeacherCard
  },
  data: function () {
		return{			
			cards: [],
			slider_wrapper: 0,
			card_width: 0,
			margin: 0,
			r_arr: true,
			l_arr: false,
			block_width: 0,
			offset: 0,
			teachers: [
				{ 
					name: 'Иван Иванов 1',
					speciality: 'ТЕСТИРОВЩИК ПО',
					info: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit',
				},
				{
					name: 'Иван Иванов 2',
					speciality: 'ТЕСТИРОВЩИК ПО',
					info: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit',
 
				},
				{
					name: 'Иван Иванов 3',
					speciality: 'ТЕСТИРОВЩИК ПО',
					info: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit',
 
				},
				{
					name: 'Иван Иванов 4',
					speciality: 'ТЕСТИРОВЩИК ПО',
					info: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit',
 
				},
				{
					name: 'Иван Иванов 5',
					speciality: 'ТЕСТИРОВЩИК ПО',
					info: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit',
				}
			]
		}				
	},
	beforeDestroy: function () {
    	window.removeEventListener('resize', this.handleResize)
    },
	methods:{	
		getNum: function(str){			
			return +str.replace(/[^\-\d]+/g, "");
		},
		getLeft: function(){
			return this.getNum(this.cards.style.left);
		},	
		getMax: function(){
			this.slider_wrapper = document.querySelector('.slider3').offsetWidth;		
			let count = this.slider_wrapper / this.offset;			
			return Math.abs(this.cards.offsetWidth - count*this.offset);
		},
		switchArrows: function(arr){
			if (arr.classList.indexOf("active") != -1){
				arr.classList.remove("active")

			}
		},
		r: function(){
			if(!this.l_arr){
				document.querySelector('.l2').classList.add("active");
				document.querySelector('.l2').classList.remove("unactive");
				this.l_arr = true;		
			}
			if(Math.abs(this.getLeft()) + this.offset < this.getMax())
				this.cards.style.left = this.getLeft() - this.offset + 'px';
			else if (Math.abs(this.getLeft()) + this.offset == this.getMax()){
				this.cards.style.left = this.getLeft() - this.offset + 'px';
				this.r_arr = false;	
				document.querySelector('.r2').classList.add("unactive");
				document.querySelector('.r2').classList.remove("active");
			}
			else{
				this.r_arr = false;	
				document.querySelector('.r2').classList.add("unactive");
				document.querySelector('.r2').classList.remove("active");
			}
		},
		l: function(){
			if(!this.r_arr){
				document.querySelector('.r2').classList.add("active");
				document.querySelector('.r2').classList.remove("unactive");
				this.r_arr = true;		
			}
			if(this.getLeft() + this.offset < 0 )
				this.cards.style.left = this.getLeft() + this.offset + 'px';
			else if (this.getLeft() + this.offset == 0){
				this.cards.style.left = this.getLeft() + this.offset + 'px';
				this.l_arr = false;	
				document.querySelector('.l2').classList.add("unactive");
				document.querySelector('.l2').classList.remove("active");
			}
			else{
				this.l_arr = false;	
				document.querySelector('.l2').classList.add("unactive");
				document.querySelector('.l2').classList.remove("active");
			}
		},		
		handleResize: function(event){
			console.log("resize");

			let slides = document.querySelectorAll('.teacher-card');

			this.cards = document.querySelector('.teacher-cards');
			
			this.card_width = document.querySelector('.teacher-card').offsetWidth; 
			this.offset = this.card_width + 15*2;
			this.cards.style.width = slides.length*this.offset + 'px';

			this.cards.style.left = 0;

			this.l_arr = false;	
			document.querySelector('.l2').classList.remove("active");
			document.querySelector('.l2').classList.add("unactive");

			this.r_arr = true;	
			document.querySelector('.r2').classList.remove("unactive");
			document.querySelector('.r2').classList.add("active");
		}
	},
	mounted(){
		let slides = document.querySelectorAll('.teacher-card');

		this.cards = document.querySelector('.teacher-cards');
		
		this.card_width = document.querySelector('.teacher-card').offsetWidth; 
		this.offset = this.card_width + 15*2;
		this.cards.style.width = slides.length*this.offset + 'px';		
		document.querySelector('.l2').classList.add("unactive");
		document.querySelector('.r2').classList.add("active");

		this.$nextTick(function() {
		window.addEventListener('resize', this.handleResize);
		});		
	},
}
</script>

<style>
	.grey_bg{
		background-color: #f6f6fa;
	}	
	.cards{
		display: inline-block;
		margin-bottom: 90px;
	}
	.l2{
		background: url(../assets/images/l_arr.png) no-repeat center top / cover;
		background-size: contain;
		text-align: left;
	}
	.r2 {
		background: url(../assets/images/r_arr.png) no-repeat center top / cover;
		background-size: contain;
		text-align: right;
	}
	.slider3{
		font-size: 0; 
		overflow: hidden;
		width: 1020px;
		margin: 0 auto;
		display: inline-block;
		vertical-align: middle;
		position: relative;
		height: 470px;
		margin-bottom: 90px;
	}
	.teacher-cards{
		display: inline-block;
		position: absolute;	
		transition: all ease 1s;
		z-index: 10; 		
 		top: 0;
 		left: 0;
	}
	@media (max-width: 1162px) {
    .slider3{
		width: 680px;
	}
}
	@media (max-width: 850px) {
    .slider3{
		width: 340px;
	}
}
	@media (max-width: 482px) {   
		.slider3{
			width: 280px;
			height: 530px;
		}		
	}

</style>