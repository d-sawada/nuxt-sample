<template>
  <div>
    <v-card :to="'/users/' + user.id">
      <v-list-item two-line>
        <v-avatar color="indigo" class="mr-5">{{ initial }}</v-avatar>
        <v-list-item-content>
          <v-list-item-title>{{ user.name }}</v-list-item-title>
          <v-list-item-subtitle>{{ user.email }}</v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>
    </v-card>
  </div>
</template>

<script>
export default {
  props: {
    user: {
      type: Object,
      required: true
    }
  },
  computed: {
    initial() {
      return this.user.name.substr(0, 1)
    }
  }
}
</script>
