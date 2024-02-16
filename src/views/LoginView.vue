<template>
	<form @submit.prevent="handleLogin">
		<h3>Login</h3>

		<div class="form-group">
			<label>Email</label>
			<input type="email" class="form-control" placeholder="Email" v-model="email" />
		</div>

		<div class="form-group">
			<label>Password</label>
			<input type="password" class="form-control" placeholder="Password" v-model="password" />
		</div>

		<button class="btn btn-primary btn-block">Login</button>
	</form>
</template>

<script>
import { useAuthStore } from '@/stores/auth.js'

export default {
	name: 'LoginView',

	data() {
		return {
			email: '',
			password: '',
		}
	},
	setup() {
		const authstore = useAuthStore()
		return { authstore }
	},
	methods: {
		async handleLogin() {
			await this.authstore.login(this.email, this.password)
			this.$router.push('/home')
		},
	},
}
</script>
