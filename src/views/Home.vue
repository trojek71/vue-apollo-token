<template>
  <div class="home">
    <ApolloMutation
    :mutation="require('../graphql/login.gql')" 
    :variables="{email,password}"
    @done="onDone"
    >
    <template v-slot="{mutate}">
      <form v-on:submit:prevent="mutate()">
        <label for="email">Email</label>
        <input v-model="email" type="email" id="email">
        <label for="password">password</label>
        <input v-model="password" type="password" id="password">
        <button @click="mutate()">Submit</button>
      </form>
    </template>
    </ApolloMutation>
    
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue'



export default {
  name: 'Home',
  data(){
    return{
    email: "",
    password:"",
    token:''
    }
  },
  
  methods :{
    onDone(val) {
      const token = val.data.login.token
      localStorage.setItem('apollo-token',token)
    }
  }
}
</script>
