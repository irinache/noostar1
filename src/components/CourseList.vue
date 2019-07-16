<template>
	<div class="container-fluid grey_bg">
		<div class="row">
			<Heading text = "Список курсов" color="grey" />			
		</div>
		
		<div class="course-cards">
				<CourseCard />
				<CourseCard />
				<CourseCard />			
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
  }
}
</script>

<style>
	.grey_bg{
		background-color: #f6f6fa;
	}	
	.course-cards{
		display: inline-block;
		margin-bottom: 90px;
	}
</style>