<template>
  <section>
    <form @submit.prevent="submitForm" class="form-validated">
      <base-input class="input-group" label="Username" v-model="formData.username" />
      <span
        class="error"
        v-for="error in v$.username.$errors"
        :key="error.$uid"
      > {{ error.$message }}
      </span>
      
      <base-input type="email" class="input-group" label="Email" v-model="formData.email" />
      
      <base-input type="password" class="input-group" label="Password" v-model="formData.password" />
      
      <base-input type="password" class="input-group" label="Confirm Password" v-model="formData.confirmPassword" />

      <button type="submit">Create User</button>
    </form>
    <div>
      <p>Erros: </p>
      <span class="error" v-for="error in v$.$errors" :key="error.$uid">
        {{ error.$property }}  -  {{ error.$message }}
      </span>
    </div>
  </section>

</template>
<script lang="ts" setup>
import { computed, reactive } from 'vue'
import BaseInput from './BaseInput.vue'
import useVuelidate, { ValidationRule, ValidatorResponse } from '@vuelidate/core'
import { required, minLength, sameAs, email, helpers } from '@vuelidate/validators'


const containsUser = (value:string) => {
  return value.includes('user')
}
const formData = reactive({
  username: "",
  email: "",
  password: "",
  confirmPassword: "",
})

const rules = computed(() => {
  return {
    username: {
      required: helpers.withMessage('Username cannot be empty', required),
      minLength: minLength(10),
      containsUser: helpers.withMessage('Field must have users', containsUser),
    },
    email: { required, email },
    password: { required },
    confirmPassword: {
      required,
      sameAs: sameAs(formData.password)
    }
  }
})

const v$ = useVuelidate(rules, formData)

const submitForm = async () => {
  // calling the function validate from Vuelidate
  // It's async to we need to add the await before
  
  const results = await v$.value.$validate()

  if(!results) {
    console.log('Form: its not submited error')
  }
  if(results) {
    console.log('Form: User has been created');
  }
}

</script>
<style scoped>
.form-validated {
  display: flex;
  flex-direction: column;
  padding: 8px 12px;
}

.input-group {
  margin: 12px 24px;
}

.form-validated button {
  width: 100px;
  height: 25px;
  margin-left: 24px;
}

.error {
  color: red;
  text-align: left;
  margin-left: 24px;
}
</style>