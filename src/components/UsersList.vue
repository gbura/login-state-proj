<template>
    <ul>
        <li v-for="user in users" :key="user.id">{{ user.id }} - {{ user.email }}</li>
    </ul>
</template>

<script>
export default {
    name: 'UsersList',
    props: ['users'],
}
</script>