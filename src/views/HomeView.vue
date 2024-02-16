<template>
	<h3>Hello</h3>
	<button @click="getUsers" class="show-users">Show Users</button>
	<UsersList :users="usersData" />
</template>

<script>
import UsersList from '@/components/UsersList.vue'
import instaceAxios from '@/axios'

export default {
	name: 'HomeView',
	components: { UsersList, UsersList },
	data() {
		return {
			usersData: [],
		}
	},
	methods: {
		async getUsers() {
			const response = await instaceAxios.get('bo/users')
			console.log(response)
		},
	},
}
</script>
