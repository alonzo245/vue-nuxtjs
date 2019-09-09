<template>
  <div>
    <form @submit.prevet="OnSubmit">
      <input type="text" nv-model="text" placeholder="Search a Post..." />
      <input type="submit" value="Search Posts" />
    </form>
  </div>
</template>

<script>
export default {
  name: "SearchPosts",
  data() {
    return {
      text: ""
    };
  },
  methods:{
      OnSubmit(){
          this.$emit('search-text', this.text)
          this.text = ""
      }
  }
};
</script>

<style>
</style>
