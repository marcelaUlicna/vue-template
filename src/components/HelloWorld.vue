<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      <span v-bind:title="loaded">
        Hover your mouse over me for a few seconds to see my dynamically bound title!
      </span>
    </p>
    <h2>Users</h2>
    <div>
      <ul>
        <li v-for="user in users" v-bind:key="user.id">
          {{user.firstname}} {{user.lastname}}
        </li>
      </ul>
    </div>
    <div>
      <input type="text" v-model="inputValue" />
      <div>
        <p>Input Value: <span v-text="inputValue"></span></p>
        <p>Input Value reverse: <span v-text="reversedMessage"></span></p>
      </div>
    </div>
    <div>
      <button class="btn btn-primary" v-on:click="counter++">Your're clicked this button {{counter}} times!</button>
    </div>
    <div>
      <p v-if="seen">Now you see me</p>
      <button class="btn btn-primary" v-on:click="toogleSeen">Toggle seen 1</button>
      <button class="btn btn-primary" @click="toogleSeen">Toggle seen 2</button>
    </div>
    <h2>Html tag</h2>
    <div>
      <p>Using mustaches: {{raw}}</p>
      <p>Using v-html directive: <span v-html="raw"></span></p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',
      loaded: 'You loaded this page on ' + new Date().toLocaleString(),
      users: [
        { id: 1, firstname: 'Sebastian', lastname: 'Eschweiler' },
        { id: 2, firstname: 'Bill', lastname: 'Smith' },
        { id: 3, firstname: 'John', lastname: 'Porter' }
      ],
      inputValue: '',
      counter: 0,
      seen: true,
      raw: '<span style="color: red;">This should be red.</span>'
    }
  },
  methods: {
    toogleSeen: function() {
      this.seen = !this.seen;
    }
  },
  computed: {
    reversedMessage: function() {
      return this.inputValue.split('').reverse().join('')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

<!-- 
Notes:
- shorthands: v-bind:href => :href, v-on:click => @click

-->
