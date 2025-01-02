<template>
  <div>
		<div class="hero-bg">
			<Header />
			<HeroSection />
		</div>
		<OrderForm />
		<StatisticsSection />
		<AchievementsSection />
		<Footer />
  </div>

</template>

<script setup>
import Header from './Header.vue'
import HeroSection from './HeroSection.vue'
import OrderForm from './OrderForm.vue'
import AchievementsSection from './AchievementsSection.vue'
import StatisticsSection from './StatisticsSection.vue'
import Footer from './Footer.vue'

import '@/css/main.scss';
</script>


<style scoped>


</style>
