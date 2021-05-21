<template>
  <form class="card w30" @submit.prevent="submitHandler">
    <div class="form-control">
      <label for="todo">Тип блока</label>
      <select name="todo" id="todo" v-model="todo">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>
    <div class="form-control">
      <label for="message">Значение</label>
      <textarea
        v-model="message"
        id="message"
         ></textarea>
    </div>
    <button class="btn" :disabled="isValid" type="submit">Добавить</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      todo: "title",
      message: "",
    };
  },
  emits: ["block"],
  methods: {
    submitHandler() {
      this.$emit("block", {
        title: this.todo,
        text: this.message,
      });
      this.message = "";
      this.todo = "title";
    },
  },
  computed: {
    isValid() {
      return this.message.length < 3;
    },
  },
};
</script>