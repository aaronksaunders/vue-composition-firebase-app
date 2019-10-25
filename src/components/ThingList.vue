<template>
  <div class="hello">
    <div v-for="item in things" :key="item">
      <div>
        <button @click="deleteThing(item)">DELETE</button>
        &nbsp;
        {{item}}
      </div>
    </div>
    <template v-if="loading">
      <h2>Processing Request...</h2>
    </template>
    <template v-else>
      <button @click="addThing('New Item: ' +new Date())">ADD</button>
    </template>
  </div>
</template>

<script>
import useThings from "../use-things";
export default {
  name: "HelloWorld",
  props: {},
  setup() {
    let thingsProps = useThings();
    return {
      // this returns all of the properties from the
      // useThings function so they are accessible in
      // in the script section and the template
      ...thingsProps
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
