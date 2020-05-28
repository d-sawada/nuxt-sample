<template>
  <div>
    <v-container>
      <v-row>
        <v-col v-for="user in users" :key="user.id" :cols="4">
          <UserCard :user="user" />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import UserCard from '../components/UserCard'

export default {
  components: {
    UserCard
  },
  async asyncData({ app, error }) {
    try {
      const users = await app.$axios.$get(
        'https://jsonplaceholder.typicode.com/users'
      )
      return { users }
    } catch (err) {
      error({
        statusCode: err.response.status,
        message: err.response.data.message
      })
    }
  }
}
</script>
