<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <button @click="handleClick">test mutation</button>
    <ul>
      <li v-for="user in users" :key="user.id">{{user.name}}</li>
    </ul>
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      users: [],
      user: null,
    }
  },
  apollo: {
    // Simple query that will update the 'hello' vue property
    users: gql`{
         users{
           name
           email
       }
    }`,
  },
  methods: {
    handleClick() {
      this.$apollo.mutate({
        // Query
        mutation: gql`mutation {
          createUser(name: "Joddddddddddddpaop", email: "susdfsaka@safjopa.ru", password: "pasasdfword") {
            id
            name
          }
        }`
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
