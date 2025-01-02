<script>
import { Field, Form, defineRule, configure } from "vee-validate";
import { required } from "@vee-validate/rules";
import { localize, setLocale } from "@vee-validate/i18n";

defineRule("required", required);

export default {
	components: { Field, Form },
  methods: {
    login() {
      console.log("Log in clicked");
    },
		async onSubmit() {
      const form = this.$refs.form;
      try {
        const isValid = await form.validate();

        if (!isValid) {
          console.log("Validation Failed");
          return;
        }
        console.log("Form Submitted");
      } catch (error) {
        console.error("Validation error:", error);
      }
    },
  },
  created() {
    configure({
      generateMessage: localize({
        en: {
          messages: {
            required: "Field {field} is required",
          },
        },
      }),
    });
    setLocale("en");
  },
};
</script>

<template>
  <header class="header">
    <div class="container">
      <a href="/" class="logo">
        <img :src="'img/svg/logo.svg'" alt="Netbook Logo" />

      </a>
      <nav class="header-nav">
        <ul class="menu">
          <li class="active"><a href="#">Home</a></li>
          <li class="dropdown">
						<a href="#community">Community</a>
						<ul class="dropdown-menu">
							<li><a href="#forums">Forums</a></li>
							<li><a href="#groups">Groups</a></li>
							<li><a href="#members">Members</a></li>
						</ul>
					</li>
          <li><a href="#">Blog</a></li>
          <li><a href="#">Events</a></li>
        </ul>
      </nav>
      <div class="auth-form">
				<Form @submit="onSubmit" class="search-form" ref="form">

					<Field
						name="search"
						:rules="{ required: 'Field search is required' }"
						v-slot="{ field, errors }"
					>
						<input
							v-bind="field"
							type="text"
							class="search-input"
							placeholder="Search Here..."
						/>
						<span class="error-message" v-if="errors.length">{{ errors[0] }}</span>
					</Field>
					<button type="submit" class="search-icon">
						<img :src="'img/svg/search.svg'" alt="Search" />
					</button>
				</Form>
				<button @click="login" class="btn btn_primary ">Log in</button>
      </div>
    </div>
  </header>
</template>

<style  lang="scss">
@use "@/css/variables.scss" as vars1;

.header {
	width: 100%;
  color: vars1.$white;
  padding: 22px 0 18px;
  display: flex;
  justify-content: space-between;
  align-items: center;
	border-bottom: 1px solid rgba(33, 123, 244, 0.1 );
	.container {
		display: flex;
		align-items: center;
		justify-content: space-between;
		@media (max-width:767px){
			flex-wrap: wrap;
		}
	}
	.logo{
		min-width: 143px;
		// transition: 0.3s;
		&:hover{
			opacity: 0.7;
		}
	}
	&-nav {
		margin: 0 auto 0 62px;
		@media (max-width: 1400px){
			margin-left: 3vw;
		}
		.menu {
			list-style: none;
			display: flex;
			gap: 1rem;
			@media (max-width:767px){
				padding: 10px 0px;
			}
			li {
				position: relative;
				&.active a{
					font-weight: 600;
					color: #2B2B39;
				}
				a {
					padding: 10px;
					color: #656464;
					text-decoration: none;
					font-size: 14px;
					font-weight: 500;
					// transition: color 0.3s;
					&:hover{
						font-weight: 600;
						color: #2B2B39;
					}
				}
			}
		}
	}
	.auth-form {
		display: flex;
		.btn{
			width: 123px;
			height: 50px;
			font-weight: 600;
		}
		.search{
			position: relative;
			&-form {
				position: relative;
				width: 105px;
				display: flex;
				align-items: center;
				padding: 0.2rem 0;
				margin-right: 40px;

				.error-text, .error-message {
					min-width: 200px;
					position: absolute;
					bottom: -12px;
					color: vars1.$errors;
					font-size: 0.9rem;
					margin-top: 8px;
					font-weight: 400;
					font-size: 12px;
				}
			}

			&-icon {
				position: absolute;
				z-index: 1;
				font-size: 1rem;
				color: #666;
				margin: 0rem;
				padding: 0;
				cursor: pointer;
				border: 0;
				background: transparent;
			}

			&-input {
				width: 100%;
				height: 100%;
				padding-left: 20px;
				border: none;
				outline: none;
				font-size: 12px;
				color: #686868;
				background: transparent;
				border-bottom: 1px solid #E5E5E5;
				&::placeholder {
					color: #aaa;
				}
			}

		}
	}

}
</style>
