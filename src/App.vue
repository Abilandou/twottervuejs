<template>
    <div id="app">
      <p>{{ user.username }} - {{ fullName }}</p>
      <strong>Followers---{{ followers }}</strong>

      <button @click="followUser">
        Follow
      </button>
    </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: 'Godlove',
        firstname: 'Abiland',
        email: 'godlove@gmail.com',
        is_admin: true
      }
    }
  },

  watch: {
    followers(newFollowerCount, oldFollowerCount){
      if(oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.username} has gained a new follower!`)
      }
    }
  },

  computed: {
    fullName(){
      return `${this.user.firstname} ${this.user.username}`
    }
  },

  methods: {
    followUser(){
      this.followers++
    }
  },

  mounted(){
    this.followUser();
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
}
</style>
