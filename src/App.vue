<template>
  <div id="app">
    <h1>{{ firstName }}</h1>
    <h2>{{ 2022 - num }}</h2>
    <h3>{{ num > 1 ? "Number: > 1" : "Number < 1" }}</h3>
    <h3>{{ obj.age }}</h3>
    <a :href="linkUrl">Link</a>
    <a :[artKey]="linkUrl">Link</a>
    <template v-if="msgIsVisible === 1">
      <div class="message">Message</div>
    </template>
    <template v-else-if="msgIsVisible >= 2">
      <div class="message">second Message</div>
    </template>
    <template v-else>
      <div class="message">Another Message</div>
    </template>
    <div v-show="isVisibleBlock">V show Example</div>
    <div class="name-input" v-if="inputNameVisible">
      <label>Name</label>
      <input type="text" placeholder="input name" key="name-input" />
    </div>
    <div class="nickname-input" v-else>
      <label>nickName</label>
      <input type="text" placeholder="input nickname" key="nickname-input" />
    </div>
    <button @click="inputNameVisible = !inputNameVisible">change form</button>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
export default {
  name: "app",
  components: {
    HelloWorld,
  },
  data: () => ({
    firstName: "Nariman",
    num: 1990,
    obj: {
      isMarried: false,
    },
    linkUrl: "https://google.com",
    artKey: "href",
    msgIsVisible: 2,
    isVisibleBlock: false,
    inputNameVisible: true,
  }),
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
