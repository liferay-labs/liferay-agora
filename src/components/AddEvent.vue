<template>
  <div class="container">
    <input v-model="title" placeholder="Title">
    <textarea v-model="message" placeholder="Content"></textarea>
    <button @click="addEvent">Add event</button>
  </div>
</template>

<script>
export default {
  name: "AddEvent",
  data: function() {
    return {
      message: "",
      title: ""
    };
  },
  methods: {
    addEvent() {
      const data = {
        contentStructure:
          "https://life-liferayagora.wedeploy.io/o/api/content-structures/34101",
        title: this.title,
        values: [{ name: "content", value: this.message }]
      };

      fetch(
        "https://life-liferayagora.wedeploy.io/o/api/content-space/20126/structured-contents",
        {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
            Authorization: "Basic <basic auth here>"
          },
          body: JSON.stringify(data)
        }
      );
    }
  }
};
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

.container {
  display: flex;
  align-items: center;
  justify-content: space-around;
  flex-direction: column;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
