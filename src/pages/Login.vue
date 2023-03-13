<template>
  <div class="form-signin w-100 m-auto">
    <h1 class="h3 mb-3 fw-normal">Please sign in</h1>

    <div class="form-floating">
      <input type="email" class="form-control" id="floatingInput" placeholder="name@example.com" v-model="state.form.email" />
      <label for="floatingInput">Email address</label>
    </div>
    <div class="form-floating">
      <input type="password" class="form-control" id="floatingPassword" placeholder="Password" v-model="state.form.password" />
      <label for="floatingPassword">Password</label>
    </div>

    <div class="checkbox mb-3">
      <label> <input type="checkbox" value="remember-me" /> Remember me </label>
    </div>
    <button class="w-100 btn btn-lg btn-primary" @click="submit()">Sign in</button>
    <p class="mt-5 mb-3 text-muted">&copy; 2017–2022</p>
  </div>
</template>

<script>
import { reactive } from 'vue'
import axios from 'axios'
export default {
  components: {},
  data() {
    return {
      sampleData: ''
    }
  },
  setup() {
    const state = reactive({
      form: {
        email: '',
        password: ''
      }
    })

    return { state }
  },
  created() {},
  mounted() {},
  unmounted() {},
  methods: {
    submit() {
      console.log(this.state.form)
      axios.post('/api/account/login', this.state.form).then((res) => {
        console.log(res)
        if (res.data != 0) window.alert('로그인 성공')
        else window.alert('로그인 실패')
      })
    }
  }
}
</script>

<style scoped>
.form-signin {
  max-width: 330px;
  padding: 15px;
}

.form-signin .form-floating:focus-within {
  z-index: 2;
}

.form-signin input[type='email'] {
  margin-bottom: -1px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}

.form-signin input[type='password'] {
  margin-bottom: 10px;
  border-top-left-radius: 0;
  border-top-right-radius: 0;
}
</style>
