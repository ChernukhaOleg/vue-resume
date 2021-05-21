<template>
  <div class="avatar">
    <img :src="$attrs.text" />
  </div>
</template>

<script>
export default {
  created() {
    console.log(this.$attrs);
  },
  mounted() {
    console.log(this.$attrs);
  },
};
</script>

<style>
.avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>