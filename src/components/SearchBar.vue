<template>
  <div class="searchBar">  
    <div class="input-group">
      <input type="text" v-on:input="onInput" class="form-control" />
      <div class="input-group-postpend">
        <button class="input-group-text" id="btnGroupAddon">search</button>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "SearchBar",
    methods: {
      onInput(e) {
        this.$emit("termChange", e.target.value);
      }
    }
  };
</script>

<style scoped>
.searchBar{
  margin-top: 20px;
  margin-bottom: 30px;
}
  .input-group-text{
    padding-right: 20px;
    padding-left: 20px;
    cursor: pointer;
  }
</style>
