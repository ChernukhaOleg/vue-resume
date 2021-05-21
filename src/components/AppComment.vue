<template>
  <div class="card" v-if="isLoad">
    <h2>Комментарии</h2>
    <hr />
    <div v-for="comm in comments" :key="comm">
      <h3>{{ comm.userName }}</h3>
      <p>{{ comm.text }}</p>
    </div>
  </div>
  <button class="btn" @click="$emit('loadComment')">
    {{ isLoad ? "Скрыть комментарии" : "Загрузить комментарии" }}
  </button>
</template>

<script>
export default {
  emits: ["loadComment"],
  props: ["comments", "isLoad"],

  created() {
    console.log(this.isLoaded);
  },
  mounted() {
    console.log(this.isLoaded);
  },
  beforeUpdate() {
    console.log(this.isLoad);
  },
};
</script>