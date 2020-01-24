<template>
  <div id="list">
    <div class="title">
      <h2 class="titleText">Upcoming Events</h2>
      <div class="underline"></div>
    </div>

    <div id="images">
      <div class="item">
        <div class="imageSlot"></div>
        <div class="date">
          <div></div>
          <div></div>
          <div></div>
        </div>
        <div class="info">
          <div></div>
          <div></div>
          <div></div>
        </div>
        <div class="button">
          <a href>Find pics ></a>
        </div>
      </div>
    </div>
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

  computed: {
    firstHalf() {
      return this.pictures.slice(4, 7);
    },

    secondHalf() {
      return this.pictures.slice(0, 3);
    }
  },

  mounted: function() {
    const api = "https://picsum.photos/v2/list";
    this.axios
      .get(api, {
        params: {
          limit: 3
        }
      })
      .then(result => {
        this.pictures = result.data;
      });
  }
};
</script>

<style lang="scss" scoped>
#list {
  background-color: white;
  width: 70%;
  height: 45%;
  border: 1px solid black;

  .title {
    padding-bottom: 25px;
    width: 40px;
    height: 30px;
    border-bottom: 2px solid #ca0188;
    border-radius: 2px;
    margin-bottom: 10px;
    position: relative;
    float: left;

    .titleText {
      width: 300px;
    }
  }

  #images {
    width: 75%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
}
</style>