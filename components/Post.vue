<template>
  <nuxt-link :to="'posts/' + id">
    <div>
      <div class="post">
        <p>{{post}}</p>
      </div>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  name: "Post",
  props: ["post", "id"]
};
</script>

<style>
.post {
  padding: 1rem;
  border: 1px dotted #ccc;
  margin: 1rem 0;
}
</style>
