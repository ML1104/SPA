<template>
  <div id="grid">
    <div>
      <h2>Hot Tickets</h2>

      <div id="images" @load="fetchPictures">
        <div v-for="picture in pictures" :key="picture.id">
          <span>{{ picture.author }}</span>
          <span>{{ picture.width }}</span>
          <span>{{ picture.height }}</span>
          <img v-bind:src="'{{ pictrue.url }}'" alt="picture" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "GridView",

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
#grid {
  background-color: white;
  width: 70%;
  height: 45%;
  border: 1px solid black;
}
</style>
