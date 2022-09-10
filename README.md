# Vue 3 + TypeScript + Vite

This small project was created to learn and apply studies about Vue3, Typescript, Vite and Form Validation usen Vuelidate and created a reusable input component

How does it works 🔍

- This project is usefull to see how quickly is Vue using Vite and understand how to apply forms validation with custom and default rules.

🌐 [Vue.js](https://vuejs.org/).

🌐 [Vite](https://vitejs.dev/)

🌐 [Vuelidate](https://vuelidate-next.netlify.app/)

---

## Setup 🏗️

```bash
npm install
npm run dev
```

### Installing Vuelidate and validations

```bash
npm install @vuelidate/core @vuelidate/validators
```

### Vuelidate setup

- After install, import to the Form using:

```tsx
import useVuelidate from '@vuelidate/core'
import { required } from '@vuelidate/validators' // import of required rule
```

- Create the rules to the form data we want to rule:

```tsx
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
```

Create the function to initializate the Vuelidade on component

```tsx
const v$ = useValidate(rules, formData)
```

### Attributes
using the v-bing="$attrs" allow us to use attributes dynamically on the componente. In this case, as we use an input element, may we need to use different types like email or password, and number as well. So on this case, binding this value we can make the things more interesting.

## Features 📜

- [x]  Create a Vue 3 app using Vite
- [x]  Create an reusable input component
- [x]  use Typescript
- [x]  Create a Form with validation use Vuelidate
