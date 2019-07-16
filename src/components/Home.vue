<template>	
	<div>
		<Header />
		<MainSlider />
		<!--<CyclicalSlider/> -->	
		<!--<Slider/>	-->	
		<!--<SliderOnePic />-->	
		<LearningPrinciples />
		<!--<CourseList />-->	
		<ThreePicSlider />
		<TeacherList />
		<ContactForm />
		<Footer />
	</div>		
</template>

<script>
import Header from './Header.vue'
import MainSlider from './MainSlider.vue'
//import SliderOnePic from './SliderOnePic.vue'
import LearningPrinciples from './LearningPrinciples.vue'
import CourseList from './CourseList.vue'
//import Slider from './slider.vue'
import CyclicalSlider from './CyclicalSlider.vue'
import TeacherList from './TeacherList.vue'
import ThreePicSlider from './ThreePicSlider.vue'
import ContactForm from './ContactForm.vue'
import Footer from './Footer.vue'

export default {
  components: {
  	Header,
  	MainSlider,
  //	Slider,
  //	SliderOnePic,
  	LearningPrinciples,
  	CourseList,
  	CyclicalSlider,
  	TeacherList,
  	ThreePicSlider,
  	ContactForm,
  	Footer
  }
}
</script>

