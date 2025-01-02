<script>
export default {
  name: "HeroSection",
};
</script>

<template>
  <section class="hero">
    <div class="container">
      <div class="hero-content">
        <div class="text-content">
			<div class="btn btn-sm">Netbook community</div>
          <h1>Your Solutions For Community!</h1>
          <p>
            More than 2 billion people in over countries use socibook to stay in touch with friends & family.
          </p>
          <div class="hero-buttons">
            <button class="btn btn_primary">About More</button>
            <button class="btn btn_secondary">Invite Friend</button>
          </div>
        </div>
        <div class="image-content">
          <img :src="'img/Iamge.png'" alt="Community Illustration" />
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss">
@use "@/css/variables.scss" as vars;

.hero {
  padding: 72px 0 82px ;
	&-content {
		display: flex;
		flex-direction: row;
		// align-items: center;
		justify-content: space-between;
		.text-content {
			max-width: 50%;
			padding-top: 51px;
			@media (max-width:767px){
				max-width: 100%;
			}
			h1 {
				font-family: vars.$interFont;
				font-size: 3.5rem;
				line-height: 1.2;
				font-weight: bold;
				margin: 20px 0 16px;
				color: #0A093D;
				@media (max-width:767px){
					font-size: 2.5rem;
				}
			}
			p {
				max-width: 500px;
				font-size: 1.125rem;
				margin-bottom: 42px;
				color: #656464;
				line-height: 1.75rem;
			}
		}
	}
	&-buttons {
		display: flex;
		gap: 18px;
	}
	.image-content{
		max-width: 50%;
		@media (max-width:767px){
			max-width: 100%;
			order: -1;
			margin-bottom: 40px;
		}
		img {
			max-width: 100%;
			height: auto;
		}
	}
}

@media (max-width: 768px) {
  .hero-content {
    flex-direction: column;
    text-align: center;
  }

  .image-content {
    max-width: 100%;
  }

  .image-content img {
    margin-top: 20px;
  }
}
</style>
