<template>
  <div id="list">
      <h2>Upcoming Events</h2>
  </div>
</template>

<script>
export default {
  name: "ListView",

  data() {
    return {
      pictures: []
    };
  },

  methods: {
    fetchPictures: function() {
      const api = "https://picsum.photos/v2/list";
      this.axios.get(api).then(result => {
        this.pictures = result.data;
      });
    }
  }
};
</script>

<style lang="scss" scoped>
#list {
  background-color: white;
  width: 70%;
  height: 45%;
  border: 1px solid black;
}
</style>