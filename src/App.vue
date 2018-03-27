<template>
  <div id="app">
    <Me title="Ender Bonnet" subtitle="Página en construcción"/>
    <div class="twitter-tl">
      <Timeline class="tweets" :id="'enbonnet'" :sourceType="'profile'" :options="{ tweetLimit: '3', theme: 'dark' }"/>
    </div>
  </div>
</template>

<script>
import Me from "./components/Me.vue";
import Timeline from "vue-tweet-embed/timeline";

export default {
  name: "app",
  components: {
    Me,
    Timeline
  }
};
</script>

<style>
html {
  background-image: url("./assets/santiago.jpg");
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
  background-repeat: no-repeat;
  background-color: #666666;
}

.twitter-tl {
  margin-top: 25px;
  width: 100%;
  display: flex;
  justify-content: center;
}

.tweets {
  width: 500px;
}
</style>
