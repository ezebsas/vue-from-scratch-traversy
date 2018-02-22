<template>
  <div class="users">
    <h1>Users</h1>
    <form v-on:submit="addUser">
      <input type="text" v-model="newUser.name" placeholder="Enter name">
      <br>
      <input type="text" v-model="newUser.email" placeholder="Enter email">
      <br>
      <input type="submit" value="Submit">
      <br>
    </form>
    <ul>
      <li v-for="user in users">
        <input type="checkbox" class="toggle" v-model="user.contacted">
        <span :class="{contacted: user.contacted}">
          {{user.name}}: {{user.email}} <button type="button" v-on:click="deleteUser(user)">X</button>
        </span>
      </li>
    </ul></li>
  </div>
</template>

<script>
  export default {
    name: 'users',
    data() {
      return {
        newUser: {},
        users:[
          {
            name: 'Sam Storms',
            contacted: false,
            email: 'sstorms@gmail.com'
          },
          {
            name: 'James White',
            contacted: false,
            email: 'white@gmail.com'
          },
          {
            name: 'John Piper',
            contacted: false,
            email: 'wiper@gmail.com'
          },
        ]
      }
    },
    methods: {
      addUser: function(e){
        this.users.push({
          name: this.newUser.name,
          contacted: false,
          email: this.newUser.email
        });
        e.preventDefault();
      },
      deleteUser: function(user) {
        this.users.splice(this.users.indexOf(user),1)
      }
    },
  }

</script>

<style scoped>
  .contacted{
    text-decoration: line-through;;
  }
</style>
