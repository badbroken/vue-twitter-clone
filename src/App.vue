<template>
  <div id="app">
    @{{ user.username }} - {{fullName}}
    <strong>Followers: </strong> {{followers}}
    <button @click="followUser">Follow</button>
  </div>

</template>

<script>


export default {
  name: 'App',
  data() {
    return{
      followers: 0,
      user: {
        username: 'vernon',
        firstName: 'Vernon',
        lastName: 'here',
        email: 'shajidvai@gmail.com',
        isAdmin: true
      }
    }
  },
  computed: {
    fullName(){
      return `${this.user.firstName} ${this.user.lastName}`
    }
  },
  watch: {
    followers(newFollowerCount, oldFollowerCount){
      if (oldFollowerCount < newFollowerCount){
        console.log(`${this.user.username} has gained a follower`)
      }
    }
  },
  methods: {
    followUser(){
      this.followers++

    }
  },
  mounted() {
    this.followUser()
  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display: flex;
  align-items: center;
  flex-direction: column;

}
</style>
