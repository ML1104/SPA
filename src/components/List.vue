<template>
  <div id="list">
    <div class="title">
      <h2 class="titleText">Upcoming Events</h2>
      <div class="underline"></div>
    </div>

    <div class="images">
      <div class="item" v-for="picture in pictures" :key="picture.id">
        <div class="imageSlot">
          <img :src="picture.download_url" alt="picture" class="image" />
        </div>
        <div class="details">
          <div class="date">
            <div>{{ picture.month }}</div>
            <div>{{ picture.day }}</div>
            <div>{{ picture.year }}</div>
          </div>
          <div class="info">
            <div>{{ picture.description }}</div>
            <div>{{ picture.author }}</div>
            <div>Width: {{ picture.width }}, Height: {{ picture.height }}</div>
          </div>
          <div class="button">
            <a href>Find pics ></a>
          </div>
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
      pictures: [],
      dates: [
        { month: "FEB", day: "14", year: "", duration: "Mon - 19:30" },
        { month: "FEB", day: "28", year: "2019", duration: "Thu - 20:00" },
        { month: "MAR", day: "01", year: "", duration: "Until Mar 03" }
      ]
    };
  },

  computed: {
    joinedArray() {
      var result = this.pictures.concat(this.dates);
      return result;
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
  height: 50%;
  display: flex;
  justify-content: space-around;
  flex-direction: column;

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

  .images {
    width: 75%;
    height: 100%;
    display: flex;
    justify-content: space-around;
    align-items: center;
    flex-direction: column;

    .item {
      display: flex;
      align-items: center;
      padding-bottom: 10px;
      padding-top: 10px;
      border-bottom: 1px solid black;
      width: 100%;

      .imageSlot {
        width: 180px;
        height: 100px;
        padding-right: 5px;

        :hover {
          cursor: pointer;
        }

        .image {
          width: 100%;
          height: 100%;
        }
      }

      .details {
        width: 100%;

        .button {
          float: right;
          padding: 10px;
          background-color: #ca0188;
          color: white;

          :link {
            text-decoration: none;
            color: white;
          }

          :visited {
            color: white;
          }
        }
      }
    }
  }
}
</style>