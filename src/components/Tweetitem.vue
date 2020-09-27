<template>
  <div class="tweet-item">
    <div class="user-tweet">
      <div class="username">
        @{{ username }}
      </div>
      <div class="tweetcontent">
        @{{ tweets.content }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Tweetitem',
  props: {
    username: {
      type: String,
      required: true
    }
    , tweets: {
      type: Object,
      required: true
    }


  }
}
</script>

<style lang="scss">

</style>