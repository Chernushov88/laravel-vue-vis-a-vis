
<template>
	<section class="achievements-section">
		<div class="container">
			<div class="achievements-cards">
				<!-- Card 1 -->
				<div class="achievement-card">
					<h3 class="title">

						<img :src="'img/svg/star.svg'" alt="star" class="star" />
						 4.8 Rating</h3>
					<div class="sub-title">
						<img :src="'img/members.png'" alt="members" class="icon" width="60" />
						<span class="primary-color">+836k</span> <span> Members</span>
					</div>
					<p class="description">
						More than 2 billion people over countries use Socibooks to stay in touch with friends.
					</p>
					<a href="#" class="link">Join Our Community &rarr;</a>
				</div>

				<!-- Card 2 -->
				<div class="achievement-card">
					<h3 class="title">
						<img :src="'img/svg/trophy.svg'" alt="trophy" class="trophy" />
						Awwwards</h3>
					<div class="sub-title">
						<img :src="'img/git-hub.png'" alt="git-hub" class="icon" />
						<p>Best of <span class="primary-color">2021</span> on Github</p></div>
					<p class="description">
						More than 2 billion people over countries use Socibooks to stay in touch with friends.
					</p>
					<a href="#" class="link">Go To Awards &rarr;</a>
				</div>

				<!-- Achievement Text -->
				<div class="achievement-text">
					<h4 class="section-title">Our Achievement</h4>
					<h3 class="headline">We are Connecting You The Digital Life.</h3>
					<p class="description">
						The scope of social media becomes crucial. It helps the business to directly engage with their needs and wants.
					</p>
					<a href="#" class="btn btn_primary">Discover me <span>&rarr;</span></a>
				</div>
			</div>
		</div>
	</section>
</template>

<script>
export default {
  name: "AchievementsSection",
};
</script>

<style lang="scss">
@use "@/css/variables.scss" as vara;

.achievements-section {
		padding: 115px 0 118px;
		background-color: #f9f9f9;
		.achievements-cards {
		display: flex;
		gap: 1.6rem;
		flex-wrap: wrap;
		align-items: flex-start;
	}
	.achievement-card {
		flex: 1;
		max-width: 336px;
		background: vara.$white;
		border-radius: 14px;
		padding: 39px 18px 38px 44px ;
		box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
		border: 1px solid rgba(185, 185, 185, 0.27);
		cursor: pointer;
		&:hover{
			background: vara.$white;
			border-color: vara.$white;
			.link {
				color: #007bff;
			}
		}
	}
	.title {
		display: flex;
		align-items: center;
		font-weight: 500;
		font-size: 1.25rem;
		margin-bottom: 2.05rem;
		img{
			margin-right: 10px;
		}
	}
	.sub-title {
		display: flex;
		align-items: center;
		color: #5D5B70;
		font-weight: 500;
		.icon{
			height: 24px;
			width: auto;
			margin-right: 16px;
		}
		.primary-color{
			font-weight: 600;
			color: vara.$primary;
		}
	}

	.description {
		font-size: 1rem;
		line-height: 1.625;
		color: #8C8C8C;
		margin: 2.5rem 0;
	}
	.link {
		color: #4A4A56;
		text-decoration: none;
		font-weight: 500;
		&:hover{
			color: #007bff;
		}
	}
	.achievement-text {
		display: flex;
        flex-direction: column;
		flex: 1.2;
		margin-left: 6%;
		text-align: left;
		padding-top: 7px;
		h3 {
			margin-top: 10px;
			font-size: 2.25rem;
			line-height: 1.334;
			font-weight: 700;
			color: #0A093D;
			font-family: "Inter", sans-serif;
		}
		.section-title {
			color: #007bff;
			font-size: 1.2rem;
		}
		.description{
			margin: 1.1rem 0 2.3rem;
			line-height: 1.725;
		}
		.btn {
			width: 192px;
			height: 58px;
			letter-spacing: -2%;
			span{
				display: inline-block;
				margin-left: 12px;
			}
		}
	}
}


</style>
