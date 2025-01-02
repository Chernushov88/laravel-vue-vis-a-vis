<template>
  <section class="form-section">
    <div class="container">
      <h3>Замовити послугу</h3>
      <Form
			 @submit="onSubmit"
        :validation-schema="schema"
        @invalid-submit="onInvalidSubmit"
      >
        <div class="form-group">
          <label for="name">Ім'я</label>
          <Field name="name" v-slot="{ field, meta }">
            <input
              v-bind="field"
							:name="field.name"
              type="text"
              id="name"
              placeholder="Введіть ім'я"
              :class="{ 'is-invalid': meta.touched && !meta.valid }"
            />
          </Field>
          <ErrorMessage name="name" class="error-text" />
        </div>

        <div class="form-group">
          <label for="surname">Прізвище</label>
          <Field name="surname" v-slot="{ field, meta }">
            <input
              v-bind="field"
							:name="field.surname"
              type="text"
              id="surname"
              placeholder="Введіть прізвище"
              :class="{ 'is-invalid': meta.touched && !meta.valid }"
            />
          </Field>
          <ErrorMessage name="surname" class="error-text" />
        </div>

				<div class="form-group">
					<label for="amount">Сума угоди</label>
					<Field name="amount" v-slot="{ field, meta }">
						<input
							v-bind="field"
							:name="field.number"
							type="number"
							id="amount"
							placeholder="Введіть суму угоди"
							:class="{ 'is-invalid': meta.touched && !meta.valid }"
						/>
					</Field>
					<ErrorMessage name="amount" class="error-text" />
				</div>

        <div class="form-group">
          <label for="code">Іпн</label>
          <Field name="code" v-slot="{ field, meta }">
            <input
              v-bind="field"
							:name="field.code"
              type="text"
              id="code"
              placeholder="Введіть код"
              :class="{ 'is-invalid': meta.touched && !meta.valid }"
            />
          </Field>
          <ErrorMessage name="code" class="error-text" />
        </div>

        <div class="form-group form-group-checkbox">
					<div class="checkbox-group">
						<Field v-slot="{ field, meta }" name="terms" type="checkbox" :value="true" :unchecked-value="false">
							<input type="checkbox" name="field.terms" id="terms" v-bind="field" :value="true" class="checkbox" :class="{ 'is-invalid': meta.touched && !meta.valid }"/>
							<label for="terms" >Погоджуюсь з правилами та умовами</label>
						</Field>
					</div>
					<div>
						<ErrorMessage name="terms" class="error-text" />
					</div>
        </div>
        <button type="submit" class="btn btn_primary">{{ buttonText }}</button>
      </Form>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";
import { Form, Field, ErrorMessage, configure } from "vee-validate";
import * as Yup from "yup";

configure({
	validateOnInput: false,
	validateOnBlur: true,
	validateOnSubmit: true
});
const schema = Yup.object({
	name: Yup
		.string()
		.required("Ім'я є обов'язковою")
		.matches(/^[\u0400-\u04FF]+(?:[-'][\u0400-\u04FF]+)*$/, "Дозволено лише кирилицю, апострофи та мінуси всередині слова")
		.min(1, "Ім'я має бути не менше 1 символів")
		.max(38, "Ім'я має бути не більше 38 символів"),
	surname: Yup
		.string()
		.required("Прізвище є обов'язковою")
		.matches(/^[\u0400-\u04FF]+(?:[-'][\u0400-\u04FF]+)*$/, "Дозволено лише кирилицю, апострофи та мінуси всередині слова")
		.min(1, "Прізвище має бути не менше 1 символів")
		.max(38, "Прізвище має бути не більше 38 символів"),
	code: Yup
		.string()
		.required("Код є обов'язковим")
		.matches(/^[0-9]+$/, "Дозволені лише цифри")
		.min(8, "Код має бути не меншше 8 символів")
		.max(10, "Код має бути не більше 10 символів"),
	amount: Yup
		.number()
		.typeError("Дозволені лише цифри")
		.optional()
		.min(1000, "Мінімальна сума — 1000")
		.max(1000000, "Максимальна сума — 1000000"),
	terms: Yup
		.boolean()
		.transform((value) => value === "on" || value === true)
		.oneOf([true], "Потрібно погодитися з правилами")
		.required("Потрібно погодитися з правилами"),
});

const buttonText = ref("Відправити");

const scrollToFirstError = (errors) => {
  const formElements = Array.from(errors.evt.srcElement.querySelectorAll("input"));
  const firstInvalidElement = formElements.find((element) =>
    element.classList.contains("is-invalid")
  );
  if (firstInvalidElement) {
    firstInvalidElement.scrollIntoView({ behavior: "smooth", block: "center" });
    setTimeout(() => firstInvalidElement.focus(), 300);
  }
};

const onSubmit = (values, { resetForm }) => {
	console.log("Valid:", values);
	buttonText.value = "Відправлено";
	setTimeout(() => {
		resetForm();
		buttonText.value = "Відправити";
	}, 5000);
};

const onInvalidSubmit = (errors) => {
	console.log("Invalid:", errors);
	scrollToFirstError(errors);
};
</script>


<style scoped lang="scss">
@use "@/css/variables.scss" as varsO;

.form-section {
  background-color: #f9fafe;
  padding: 86px 0 83px;
	font-family: varsO.$interNotoSans;
	.container {
		max-width: 594px;
		margin: 0 auto;
	}

	h3 {
		font-family: varsO.$interNotoSans;
		text-align: center;
		font-size: 2.25rem;
		margin-bottom: 64px;
		font-weight: 700;
		color: #000;
		letter-spacing: 2px;
	}

	form {
		display: flex;
		flex-direction: column;
	}

	.form-group {
		display: flex;
		flex-direction: column;
		margin-bottom: 32px;
		label {
			margin-bottom: 8px;
			font-weight: 600;
			line-height: 1.125rem;
			font-size: 12px;
			color: #666666;
		}

		input[type="text"],
		input[type="number"] {
			width: 100%;
			height: 56px;
			padding-left: 16px;
			border: 1px solid #ccc;
			border-radius: 8px;
			color: #333;
			transition: background-color 0s ease;
			&::placeholder{
				font-size: 16px;
				color: #666666;
			}
		}

		input.error {
			border-color: varsO.$errors;
		}

		.error-text {
			color: varsO.$errors;
			font-size: 0.9rem;
			margin-top: 12px;
			font-weight: 400;
			font-size: 12px;
		}

		.is-invalid {
			border: 2px solid varsO.$errors !important;
			background: url(@/assets/img/svg/error-icon.svg) no-repeat 95% center;
		}
		&.form-group-checkbox{
			margin-bottom: 23px;
		}
		.checkbox-group {
			display: flex;
			align-items: center;
    	flex-direction: row;
			.checkbox + label{
				line-height: 1.6em;
				font-size: 1em;
				font-weight: 400;
    		letter-spacing: 0.6px;
			}
		}

	}
	.btn {
		width: 172px;
		height: 56px;
		margin: 0 auto;
		border-radius: 8px;
	}
}

</style>
