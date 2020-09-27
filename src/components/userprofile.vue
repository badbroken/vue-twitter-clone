<template>
  <div class="user-prof">
    @{{ user.username }} - {{ fullName }}
    <div class="admin-badge" v-if="user.isAdmin">
      admin
    </div>
    <div class="user-badge" v-else>
      User
    </div>
    <strong>Followers: </strong> {{ followers }}
    <button @click="followUser">Follow</button>
    <div class="tweets-wrapper">
      <div class="profile-tweet" v-for=" tweet in user.tweets" :key="tweet.id">
        {{ tweet.content }}
      </div>
    </div>
  </div>
</template>

<script>
import Tweetitem from "./Tweetitem";

export default {
  name: "userprofile",
  data() {
    return {
      followers: 0,
      user: {
        username: 'vernon',
        firstName: 'Vernon',
        lastName: 'here',
        email: 'shajidvai@gmail.com',
        isAdmin: true,
        tweets: [
          {content: "What is life"},
          {
            content: "Dont jhrt me"
          }
        ]

      }
    }
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`
    }
  },
  watch: {
    followers(newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.username} has gained a follower`)
      }
    }
  },
  methods: {
    followUser() {
      this.followers++

    }
  },
  mounted() {
    this.followUser()
  }
}
</script>

<style lang="scss">
.user-prof {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display: flex;
  align-items: center;
  flex-direction: column;

  .admin-badge, .user-badge {
    background-color: #663399;
    color: white;
    border-radius: 5px;
    font-size: 1rem;
    padding: 0.3rem;
  }

  .user-badge {
    background-color: #2c3e50;
  }
}
</style>