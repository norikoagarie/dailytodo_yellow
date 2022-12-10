<template>
  <div class="page-wrap">
    <h1 class="app-name">することを入力しましょう</h1>

    <div class="form">
      <div class="form-to-do">
        <label for="" class="form__label">すること</label>
        <input v-model="task.title" type="text" name="title" class="form-to-do__input">
      </div>
      <div class="form-time-wrap">
        <div class="form-time">
          <label for="" class="form__label">始める時間</label>
          <input v-model="task.start" type="time" name="start" class="form-time__input">
        </div>
        <div class="form-time">
          <label for="" class="form__label">終わりの時間</label>
          <input v-model="task.end" type="time" name="end" class="form-time__input">
        </div>
      </div>
      <button @click="submit" class="submit" :class="{disabled: nullCheck}" type="submit" :disabled="nullCheck">OK</button>
    </div>
  </div> 
</template>

<script>
import { mapActions } from "vuex";
export default {
  name: "FormView",
  data() {
    return {
      task: {
        title: "",
        start: "",
        end: "",
      },
    };
  },
  methods: {
    submit() {
      this.addTask(this.task);
      this.$router.push({name: 'list'})
      this.task = {}
    },
    ...mapActions(["addTask"]),
  },
  computed: {
    nullCheck() {
      return (
        this.task.title === "" || this.task.start === "" || this.task.end === ""
      );
    },
  },
};


</script>

<style lang="scss" scoped>
.page-wrap {
  padding: 72px 0;
}

.app-name {
  color: #ffffff;
  font-size: 24px;
  font-family: Kaisei Opti;
  text-align: center;
  margin-bottom: 48px;
}

.form {
  background-color: #ffffff;
  border-radius: 2px;
  box-shadow: 0px 3px 6px rgba($color: #000000, $alpha: 0.16);
  height: 300px;
  width: 300px;
  margin: 0 auto;
  padding: 30px;
  display: flex;
  flex-flow: column;
  justify-content: space-between;
}

.form__label {
  color: #404040;
  display: block;
  font-size: 12px;
  font-family: Kaisei Opti;
  margin-bottom: 4px;
}

.form-to-do__input {
  border: none;
  border-bottom: 1px solid rgba($color: #404040, $alpha: 0.16);
  width: 100%;
  font-size: 1px;
}

input[type="text"]:focus {
  outline: 0;
}

.form-time-wrap {
  display: flex;
  justify-content: space-between;
}

.form-time__input {
  height: 32px;
  width: 112px;
  border-color: rgba($color: #404040, $alpha: 0.5);
  border-radius: 2px;
  font-size: 14px;
  font-family: Kaisei Opti;
}

.submit {
  background-color: #4193a1;
  border-radius: 50px;
  border: none;
  color: #ffffff;
  font-size: 14px;
  font-family: Kaisei Opti;
  font-weight: bold;
  display: block;
  height: 32px;
  width: 240px;

  &.disabled{
    opacity: 0.5;
  }
}
</style>
