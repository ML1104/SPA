<template>
  <div id="grid">
    <div class="title">
      <h2 class="titleText">Hot Tickets</h2>
      <div class="underline"></div>
    </div>

    <div class="images" v-for="picture in firstHalf" :key="picture.id">
      <div class="item" v-for="picture in secondHalf" :key="picture.id">
        <div class="imageSlot">
          <img :src="picture.download_url" alt="picture" class="image"/>
          <div class="imageText">{{ picture.author }}</div>
        </div>
        <div class="subText">
          <div>Width: {{ picture.width }}</div>
          <div>Height: {{ picture.height }}</div>
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
          limit: 6
        }
      })
      .then(result => {
        this.pictures = result.data;
      });
  }
};
</script>

<style lang="scss" scoped>
#grid {
  background-color: white;
  width: 70%;
  height: 50%;
  display: flex;
  flex-direction: column;

  .title {
    padding-bottom: 25px;
    width: 37px;
    height: 30px;
    border-bottom: 2px solid #ca0188;
    border-radius: 2px;
    margin-bottom: 10px;
    position: relative;
    float: left;

    .titleText {
      width: 200px;
    }
  }

  .images {
    display: flex;
    width: 100%;
    height: 100%;

    .item {
        box-shadow: 0px 0px 5px #000000;
        width: 200px;
        max-height: 120px;
        display: flex;
        flex-direction: column;
        margin-right: 20px;
        margin-top: 10px;
        padding-bottom: 50px;
        position: relative;
        border-radius: 2px;
        
        :hover {
          cursor: pointer;
        }

      .imageSlot {
        position: relative;
        display: flex;
        justify-content: center;
        width: 200px;

        img {
          width: 200px;
          height: 120px;
        }

        .imageText {
          position: absolute;
          bottom: 0;
          left: 0;
          width: 95%;
          background-color: rgba($color: #000000, $alpha: 0.3);
          padding: 5px;
          color: white;
        }
      }

      .subText {
        padding: 5px;
      }
    }
  }
}
</style>
