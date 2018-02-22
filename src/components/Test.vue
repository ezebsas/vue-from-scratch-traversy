<template>
  <div class="test">
    <input type="text" v-model="title">
    <br>
    <h1 v-text="title"></h1>
    <p v-if="showName">{{user.firstName}}</p>
    <p v-else>Nobody</p>
    <ul>
      <li v-for="item in items">
        {{item.title}}
      </li>
    </ul>
    <button type="button" v-on:click="greet">Say hello</button>
    <br>
    <input type="text" v-on:keyup="presskey" v-on:keyup.enter="enterhit">
    <hr>
    <label>First name:</label><input type="text" v-model="user.firstName">
    <br>
    <label>Last name:</label><input type="text" v-model="user.lastName">
    <br>
    <h3>Full name: {{fullname}}</h3>
    <p>{{msg}}</p>
  </div>
</template>

<script>
  export default {
    name: 'test',
    props: {
      msg: {
        type: String,
        default: 'foobar'
      }
    },
    data() {
      return {
        title: 'Hello world',
        user: {
          firstName: 'John',
          lastName: 'Doe'
        },
        showName: true,
        items: [
          {title: 'Item One'},
          {title: 'Item Two'},
          {title: 'Item Three'},
        ],
      }
    },
    methods: {
      greet: function(){
        alert('hello');
      },
      presskey: function(e){
        console.log(e.target.value);
      },
      enterhit: function(e){
        console.log('enter');
      }
    },
    computed: {
      fullname: function(){
        return this.user.firstName + ', ' + this.user.lastName;
      }
    }
  }

</script>

<style scoped>

</style>
