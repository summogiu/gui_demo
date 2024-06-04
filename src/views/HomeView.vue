<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <VForm @submit="onSubmit" v-slot="{ errors, values }">
      {{ errors }} {{ values }}
      <VField name="可自訂義的名稱" type="text" placeholder="Who are you"
      class="form-control" :class="{ 'is-invalid': errors['可自訂義的名稱'] }"
      rules="email|required" v-model="user.email"></VField>
      <ErrorMessage name="可自訂義的名稱" class="invalid-feedback"></ErrorMessage> <!--這個name會對應到指定的name 顯示他的:rules所回傳的結果-->

      <button>Submit</button>
    </VForm>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  },
  data () {
    return {
      user: {
        email: ''
      }
    }
  },
  methods: {
    onSubmit () {
      console.log(this.user)
    }
  },
  created () {
    console.log(this)
  }
}
</script>
