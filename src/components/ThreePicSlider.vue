<template>
	<div class="container-fluid grey_bg">
		<div class="row">
			<Heading text = "Список курсов" color="grey" />			
		</div>
		<div class="arr2 l" v-on:click = "l">
				
		</div>
		<div class="slider2">
			<div class="course-cards2" >
				<CourseCard v-for="course in courses"
				v-bind:key="course.course_name"
				v-bind:date="course.date" v-bind:course_name="course.course_name"
				v-bind:duration="course.duration"
				v-bind:price="course.price"
				v-bind:teacher="course.teacher"
				/>		
			</div>	
		</div>
						
		<div class="arr2 r" v-on:click = "r">
				
		</div>
	</div>
</template>

<script>
import Heading from './heading.vue'
import CourseCard from './CourseCard.vue'
export default {
  components: {
  	Heading,
  	CourseCard
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
			courses: [
				{ 
					date: '23.05.2019',
					course_name: 'Объектно-ориентированное программирование',
					duration: '70 часов',
					price: '5000 грн',
					teacher: 'Козаченко А. А.'
				},
				{
					date: '26.06.2019',
					course_name: 'Тестирование',
					duration: '74 часов',
					price: '5500 грн',
					teacher: 'Иванов В. В.'
 
				},
				{
					date: '28.06.2019',
					course_name: 'Операционные системы',
					duration: '65 часов',
					price: '6500 грн',
					teacher: 'Петров И. И.'
 
				},
				{
					date: '06.08.2019',
					course_name: 'Веб-дизайн',
					duration: '80 часов',
					price: '7500 грн',
					teacher: 'Сидоров В.К.'
 
				},
				{
					date: '29.09.2019',
					course_name: 'Java Core',
					duration: '60 часов',
					price: '5000 грн',
					teacher: 'Иванов В. В.' 
				}
			]
		}				
	},
	computed:{
		
	},
	ready: function(){
		
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
			this.slider_wrapper = document.querySelector('.slider2').offsetWidth;		
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
				document.querySelector('.l').classList.add("active");
				document.querySelector('.l').classList.remove("unactive");
				this.l_arr = true;		
			}
			if(Math.abs(this.getLeft()) + this.offset < this.getMax())
				this.cards.style.left = this.getLeft() - this.offset + 'px';
			else if (Math.abs(this.getLeft()) + this.offset == this.getMax()){
				this.cards.style.left = this.getLeft() - this.offset + 'px';
				this.r_arr = false;	
				document.querySelector('.r').classList.add("unactive");
				document.querySelector('.r').classList.remove("active");
			}
			else{
				this.r_arr = false;	
				document.querySelector('.r').classList.add("unactive");
				document.querySelector('.r').classList.remove("active");
			}
		},
		l: function(){
			if(!this.r_arr){
				document.querySelector('.r').classList.add("active");
				document.querySelector('.r').classList.remove("unactive");
				this.r_arr = true;		
			}
			if(this.getLeft() + this.offset < 0 )
				this.cards.style.left = this.getLeft() + this.offset + 'px';
			else if (this.getLeft() + this.offset == 0){
				this.cards.style.left = this.getLeft() + this.offset + 'px';
				this.l_arr = false;	
				document.querySelector('.l').classList.add("unactive");
				document.querySelector('.l').classList.remove("active");
			}
			else{
				this.l_arr = false;	
				document.querySelector('.l').classList.add("unactive");
				document.querySelector('.l').classList.remove("active");
			}
		},		
		handleResize: function(event){
			let slides = document.querySelectorAll('.course-card');

			this.cards = document.querySelector('.course-cards2');
			
			this.card_width = document.querySelector('.course-card').offsetWidth; 
			this.offset = this.card_width + 15*2;
			this.cards.style.width = slides.length*this.offset + 'px';

			this.cards.style.left = 0;

			this.l_arr = false;	
			document.querySelector('.l').classList.remove("active");
			document.querySelector('.l').classList.add("unactive");

			this.r_arr = true;	
			document.querySelector('.r').classList.remove("unactive");
			document.querySelector('.r').classList.add("active");
		}
	},
	mounted(){
		let slides = document.querySelectorAll('.course-card');

		this.cards = document.querySelector('.course-cards2');
		
		this.card_width = document.querySelector('.course-card').offsetWidth; 
		this.offset = this.card_width + 15*2;
		this.cards.style.width = slides.length*this.offset + 'px';

		document.querySelector('.l').classList.add("unactive");
		document.querySelector('.r').classList.add("active");

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
	.course-cards2{
		display: inline-block;
		position: absolute;	
		transition: all ease 1s;
		z-index: 10;
 		text-align: left;
 		top: 0;
 		left: 0;
	}
	.slider2{
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
	.arr2{		
		width: 50px;
		height: 50px;
		display: inline-block;
		vertical-align: middle;
		opacity: 0.7;
	}
	.active:hover {
		opacity: 1;
	}
	.unactive{
		opacity: 0.3;
	}
	.active{
		opacity: 0.7;
	}
	.l{
		background: url(../assets/images/l_arr.png) no-repeat center top / cover;
		background-size: contain;
		text-align: left;
	}
	.r {
		background: url(../assets/images/r_arr.png) no-repeat center top / cover;
		background-size: contain;
		text-align: right;
	}
	@media (max-width: 1162px) {
    .slider2{
		width: 680px;
	}
}
	@media (max-width: 850px) {
    .slider2{
		width: 340px;
	}
}
	@media (max-width: 482px) {   
		.slider2{
			width: 280px;
			height: 530px;
		}
		.arr2{		
			width: 30px;
			height: 30px;		
		}
	}
	@media (max-width: 380px) {  
		.arr2{		
			width: 10px;
			height: 30px;		
		}
	}
</style>