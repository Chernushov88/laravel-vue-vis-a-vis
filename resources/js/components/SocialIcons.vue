<template>
	<ul class="social-icons">
		<li v-for="icon in icons" :key="icon.name">
			<div class="icons-wrapp">
				<a
                    :href="icon.link"
                    target="_blank"
                    rel="noopener noreferrer">
					<img
                        :src="icon.path"
                        :alt="icon.name"
                        class="icon"
                    />
				</a>
			</div>
		</li>
	</ul>
</template>

<script>

export default {
  name: "SocialIcons",
  data() {
    return {
      icons: [
        {
          name: "Twitter",
          path: "img/svg/social/twitter.svg",
          link: "https://twitter.com",
        },
        {
          name: "Instagram",
          path: "img/svg/social/instagram.svg",
          link: "https://instagram.com",
        },
        {
          name: "Facebook",
          path: "img/svg/social/facebook.svg",
          link: "https://facebook.com",
        },
        {
          name: "Linkedin",
          path: "img/svg/social/linkedin.svg",
          link: "https://linkedin.com",
        },
      ],
    };
  },
};
</script>

<style scoped lang="scss">
@use "@/css/variables.scss" as varsS;

.social-icons{
	display: flex;
	li{
		padding: 4px;
	}
	.icons-wrapp {
		width: 36px;
		height: 36px;
		display: flex;
		justify-content: center;
		align-items: center;
		border-radius: 50%;
		background-color: varsS.$white;
		cursor: pointer;
		&:hover {
			background-color: varsS.$primary;
			.icon {
				color: varsS.$white;
			}
		}
		.icon {
			width: 18px;
			height: 18px;
			color: #000;
		}
	}
}

</style>
