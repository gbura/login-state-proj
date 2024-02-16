<template>
	<nav class="navbar navbar-expand navbar-light fixed-top">
		<div class="container">
			<router-link to="/home" class="navbar-brand">Home</router-link>
			<div class="collapse navbar-collapse">
				<ul class="navbar-nav ml-auto">
					<template v-if="isAuthenticated()">
						<li class="nav-item">
							<router-link to="/login" class="nav-link">Login</router-link>
						</li>
						<li class="nav-item">
							<router-link to="/register" class="nav-link">Sign up</router-link>
						</li>
					</template>
					<template v-else>
						<li class="nav-item">
							<button @click="handleLogOut" class="nav-link">Log out</button>
						</li>
					</template>
				</ul>
			</div>
		</div>
	</nav>
</template>

<script>
import { useAuthStore } from '@/stores/auth.js'

export default {
	name: 'TheNavbar',
	setup() {
		const authstore = useAuthStore()
		return { authstore }
	},
	methods: {
		isAuthenticated() {
			return !this.authstore.isAuthenticated
		},
		handleLogOut() {
			this.authstore.logout()
			this.$router.push('/login')
		},
	},
}
</script>
