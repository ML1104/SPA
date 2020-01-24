<template>
  <div id="header">
    <form action>
      <input type="search" name="search" id="search" />
      <input type="submit" id="submit" value="Search" />
    </form>
  </div>
</template>

<script>
export default {
  name: "PageHeader"
};
</script>

<style lang="scss" scoped>
#header {
  background-color: black;
  width: 100%;
  height: 50px;
  text-align: center;

  form {
    padding: 5px;

    #search {
      padding: 5px;
      width: 300px;
    }

    #submit {
      background-color: #CA0188;
      color: white;
      border: 0;
      padding: 7px;
    }
  }
}
</style>
