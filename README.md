# Vue 3 + TypeScript + Vite

### Run this project
npm run dev

### install vuelidate and validations
npm install @vuelidate/core @vuelidate/validators

### Vuelidate setup
- After install, import to the Form using:
import useVuelidate from '@vuelidate/core'
import { required } from '@vuelidate/validators'

- Create the rules to the form data we want to rule
const formData = reactive({
  username: "",
  email: "",
  password: "",
  confirmPassword: "",
})

const rules = {
  username: { required },
  email: { required },
  password: { required },
  confirmPassword: { required }
}

- Create the function to initializate the Vuelidate on component
const v$ = useValidate(rules, formData)