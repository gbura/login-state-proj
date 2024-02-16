<template>
	<form @submit.prevent="handleRegister" v-if="!isRegistered">
		<h3>Rejestracja</h3>

		<div class="form-group">
			<label>Name</label>
			<input type="text" class="form-control" placeholder="Name" v-model="name" />
		</div>

		<div class="form-group">
			<label>Email</label>
			<input type="email" class="form-control" placeholder="Email" v-model="email" />
		</div>

		<div class="form-group">
			<label>Password</label>
			<input type="password" class="form-control" placeholder="Password" v-model="password" />
		</div>

		<button class="btn btn-primary btn-block">Rejestruj</button>
	</form>

	<p v-else>Udało się zarejestrować! Potwierdź adres e-mail na swojej skrzynce w celu kontynuacji.</p>
</template>

<script>
import { useAuthStore } from '@/stores/auth.js'

export default {
	name: 'RegisterView',
	setup() {
		const authstore = useAuthStore()
		return { authstore }
	},
	data() {
		return {
			name: '',
			email: '',
			password: '',
			isRegistered: false,
		}
	},
	methods: {
		async handleRegister() {
			const response = await this.authstore.register(this.email, this.password, this.name)
			this.isRegistered = response.success
		},
	},
}
</script>
