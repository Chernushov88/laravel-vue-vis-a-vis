<template>
  <footer class="footer">
    		<div class="footer-top">
			<div class="container ">
				<div class="grid">
					<div class="footer-column">
						<h4>Home</h4>
						<ul>
							<li><a href="#">Home</a></li>
							<li><a href="#">Community</a></li>
							<li><a href="#">Events</a></li>
							<li><a href="#">Contact</a></li>
						</ul>
					</div>
					<div class="footer-column">
						<h4>Resources</h4>
						<ul>
							<li><a href="#">Blog</a></li>
							<li><a href="#">News</a></li>
							<li><a href="#">Guides</a></li>
							<li><a href="#">Help Center</a></li>
						</ul>
					</div>

					<div class="footer-column">
						<h4>Community</h4>
						<ul>
							<li><a href="#">NewsFeed</a></li>
							<li><a href="#">Profile</a></li>
							<li><a href="#">Friends</a></li>
							<li><a href="#">Forums</a></li>
						</ul>
					</div>

					<div class="footer-column">
						<h4>Main Links</h4>
						<ul>
							<li><a href="#">Members</a></li>
							<li><a href="#">Activity</a></li>
							<li><a href="#">Groups</a></li>
							<li><a href="#">Private Group</a></li>
						</ul>
					</div>
				</div>


        <div class="subscribe-column">
   					       <h4>Subscribe Cirkle <br>Newsletter</h4>
          <p>Subscribe to be the first one to know about updates. Enter your email</p>
          <form @submit.prevent="subscribe">
            <div class="subscribe-input">
              <input type="email" placeholder="Email Address" v-model="email" />
              <button type="submit">Subscribe</button>
            </div>
          </form>
        </div>
      </div>
    </div>
		<div class="footer-bottom">
			<div class=     "container flex">
				<p>Bespik Creative Agency</p>
				<a class="logo" href="#">
					<img :src="'img/svg/logo-footer.svg'" alt="Netbook Logo" />
				</a>
        <SocialIcons />
			</div>
		</div>
  </footer>
</template>

<script>
 import SocialIcons from "./SocialIcons.vue";

export default {
  name: "Footer",
  components: {
    SocialIcons
  },
  data() {
    return {
      email: ''
    };
  },
  methods: {
    subscribe() {
      if (this.email) {
        alert(`Subscribed with: varsF.${this.email}`);
        this.email = '';
      } else {
        alert('Please enter a valid email address.');
      }
    }
  }
};
</script>

<style lang="scss">
@use "@/css/variables.scss" as varsF;

.footer {
  background-color: #2B2B39;
  color: #E7E7E7;
	&-top {
		padding: 58px 0 65px;
		.container{
			display: flex;
			justify-content: space-between;
	  		flex-wrap: wrap;
			h4 {
				margin-bottom: 1rem;
				font-weight: 500;
				font-size: 1.25rem;
				color: varsF.$white;
			}
		}
		.grid{
			display: grid;
			grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
			width: 668px;
			@media (max-width:767px){
				display: block;
			}
			.footer-column {
				padding: 20px 0;
				h4 {
					margin-bottom: 1.375rem;
				}
				ul {
					padding: 0;
					margin: 0;
					line-height: 2.875rem;
					li {
						a {
							color: #E7E7E7;
							text-decoration: none;
							&:hover {
								color: #00aaff;
							}
						}
					}
				}
			}
		}

		.subscribe{
			&-column{
				max-width: 340px;
				padding: 16px 0;
				h4{
					margin-bottom: 0;
					line-height: 2rem;
				}
						@media (max-width:767px){
					max-width: 100%;
				}
				p {
					margin: 1rem 0 2rem;
					line-height: 1.75rem;
				}
			}
			&-input {
				position: relative;
				display: flex;
				width: 100%;
				height: 48px;

				input {
					width: 100%;
					height: 100%;
					padding: 0 128px 0 24px;
					font-size: 0.75rem;
					border: 0;
					outline: 1px solid varsF.$white;
					border-radius: 12px;
					background: transparent;
					color: varsF.$white;
					&::placeholder{
						font-size: 0.75rem;
						color: #717179;
					}
				}

				button {
					position: absolute;
					right: 0;
					top: 0;
					z-index: 9;
					width: 128px;
					height: 100%;
					color: #2B2B39;
					border: none;
					border-radius: 12px;
					cursor: pointer;
					background: varsF.$white;
					// transition: 0.3s;
					&:hover {
						// background-color: #0088cc;
						opacity: 0.7;
					}
				}
			}
		}
	}

	&-bottom {
		padding: 26px 0;
		background: #20202D;
		.flex{
			display: flex;
			justify-content: space-between;
			align-items: center;
		}
	}
	.logo{
			&:hover{
			opacity: 0.7	;
		}
	}

}
</style>
