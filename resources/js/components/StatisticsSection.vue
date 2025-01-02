<template>
  <section class="statistics">
    <div class="container">
			<div class="top-block">
				<h2>Search through more than 11 million social media profiles</h2>
				<div class="text">Heepsy’s search filters help you find exactly what you’re looking for, and our influencer reports provide you with the metrics</div>
			</div>
			<div class="statistics-grid">
        <div class="stat-item">
          <div class="h2">2260</div>
          <p>Satisfied Brands</p>
        </div>
        <div class="stat-item">
          <div class="h2">1324</div>
          <p>Satisfied Clients</p>
        </div>
        <div class="stat-item">
          <div class="h2">3453</div>
          <p>Sponsored</p>
        </div>
        <div class="stat-item">
          <div class="h2">9786</div>
          <p>Completed</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "StatisticsSection",
};
</script>

<style scoped lang="scss">
@use "@/css/variables.scss" as varsST;

.statistics {
  background-color: #231A36;
  color: varsST.$white;
  padding: 122px 0 120px;
	font-family: 'Poppins', sans-serif;
	.top-block{
		max-width: 734px;
		margin: 0 auto;
		text-align: center;
		h2 {
			margin-bottom: 18px;
			line-height: 1.25em;
			font-size: 2.5em;
			font-weight: 600;
			color: varsST.$white;
		}
		.text{
			max-width: 600px;
			margin: 0 auto 110px;
			line-height: 1.75rem;
			color: #7B9292;
		}
	}

	.statistics-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
		gap: 20px;
		max-width: 1000px;
		margin: 0 auto;
		text-align: center;
		cursor: pointer;
		.stat-item {
			// transition: 0.3s;
			.h2{
				margin-bottom: 10px;
				font-size: 2.5em;
				font-weight: 600;
				color: varsST.$white;
			}
		}

		.stat-item:hover {
			transform: translateY(-5px);
			box-shadow: 0 6px 10px rgba(0, 0, 0, 0.15);
		}

		p {
			font-size: 1rem;
			color: #7B9292;
		}
	}
}


</style>
