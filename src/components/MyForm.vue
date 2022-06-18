<template>
  <div>
    <input ref="el" type="text" placeholder="Name" v-model="name" >
    <div>
      <button :disabled="!name.length" @click="submitForm">Submit</button>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent, ref, onMounted } from 'vue'

export default defineComponent({
  setup() {
    const name = ref('')
    const el = ref()
    
    onMounted(() => {
      el.value.focus()
    })

    const submitForm = ():void => {
      console.log(`Name: ${name.value}`)
    }
    return {
      el,
      name,
      submitForm
    }
  }
})
</script>

<style scoped>
input[type='text'] {
  padding: 5px;
}

button {
  margin-top: 20px;
}
</style>