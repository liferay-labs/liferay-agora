<template>
  <div class="hello">
    <ul>
      <li v-for="meetup in meetups" :key="meetup.title">{{meetup.title}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data: function() {
    return {
      meetups: []
    };
  },
  mounted() {
    this.fetchItems();
  },
  methods: {
    fetchItems() {
      fetch(
        `https://life-liferayagora.wedeploy.io/o/api/content-space/20126/structured-contents`
      )
        .then(stream => stream.json())
        .then(stream => {
          console.log(stream);
          return stream;
        })
        .then(data => (this.meetups = data._embedded.StructuredContent))
        .catch(error => console.error(error));
    }
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
