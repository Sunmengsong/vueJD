<template>
  <div class="content">
    <indexSearch></indexSearch>
    <indexFooter></indexFooter>
  </div>
</template>

<script>
import indexSearch from "../components/index-search";
import indexFooter from "../components/indexFooter";
export default {
  data() {
    return {};
  },
  components: {
    indexSearch,
    indexFooter
  },
  beforeMount() {
    console.log(this);
  }
};
</script>

<style>
.content {
  background-color: #f4f4f4;
  height: 3000px;
}
</style>