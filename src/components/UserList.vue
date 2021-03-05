<template>
  <table class="table">
    <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col" @click="test">Name</th>
      <th scope="col">Email</th>
      <th scope="col">Age</th>
    </tr>
    </thead>
    <tbody>
    <tr
    v-for="(user, i) of users">
      <th scope="row">{{i+1}}</th>
      <td>{{user.name | toUpper}}</td>
      <td>{{user.email}}</td>
      <td>{{user.age}}</td>
    </tr>
    </tbody>
  </table>
</template>

<script>
export default {
name: "UserList",
props: ['users'],
methods: {
  test() {
    console.log(this.users);
  }
},
filters: {
  toUpper(val) {
    return val[0].toUpperCase() + val.slice(1);
  }
}
}
</script>

<style scoped>

</style>