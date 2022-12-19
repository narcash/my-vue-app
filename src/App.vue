<template>
  <div id="app">
    <HelloWorld :title="title" @onChangeCounter="onChangeCounterComponent" />
    <!-- <button @click.right="onClick('some value', $event)">Click event</button> -->
    <!-- <a href @click.prevent="onLinkClick">Link</a> -->
    <!-- <h1>{{ text }}</h1>
    <h3 class="title" :class="clasObj">Hello {{ fullName }}!</h3>
    <input type="text" @keyup.enter="setName" /> -->
    <!-- <input type="text" @keyup.enter="onKeyUp" /> -->
    <ul>
      <!-- <li v-for="(value, name, index) in product" :key="index">
        {{ name }} : {{ value }}
      </li> -->
      <!-- <li v-for="(color, index) in colors" :key="color">
        {{ index + 1 }} {{ color }}
      </li> -->
      <!-- <li v-for="user in users" :key="user.id">
        {{ user.name }} : {{ user.age }}
      </li> -->
      <div>
        <!-- <input type="text" @keyup.enter="addNewColor" /> -->
        <!-- <input type="text" @keyup.enter="deleteProp" /> -->
      </div>
    </ul>
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
    title: "Some title",
  }),
  computed: {
    clasObj() {
      return {
        "active-class": this.isActive,
        error: !this.isActive,
      };
    },
    fullName: {
      get() {
        return `${this.firstName || "Default"} ${this.lastName || "User"}`;
      },
      set(value) {
        console.log(value);
        const [firstName, lastName] = value.split(" ");
        console.log(firstName, lastName);
        this.firstName = firstName;
        this.lastName = lastName;
      },
    },
  },
  methods: {
    onClick(value, e) {
      console.log(value, e);
    },
    onLinkClick() {
      console.log("link click");
    },
    onKeyUp(e) {
      console.log(e);
      this.text = e.target.value;
    },
    addNewColor(e) {
      console.log(this);
      // this.colors.push(e.target.value);
      // this.colors[this.colors.length] = e.target.value;
      this.$set(this.colors, this.colors.length, e.target.value);
    },
    deleteProp(e) {
      // delete this.product[e.target.value];
      console.log(e.target.value);
      this.$delete(this.product, e.target.value);
    },
    setName(e) {
      this.fullName = e.target.value;
    },
    onLastNameUpdate(value) {
      console.log("watch", value);
    },
    onChangeCounterComponent(value) {
      console.log("In App.vue, counter: ", value);
    },
  },
  watch: {
    lastName: "onLastNameUpdate",
  },
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
