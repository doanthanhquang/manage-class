<template>
  <div class="create-class-container">
    <button class="close-button" @click="closeEdit">X</button>
    <h2>Edit Class</h2>
    <div class="input-group">
      <input type="text" v-model="editItem.name" placeholder="Name..." />
      <input type="text" v-model="editItem.address" placeholder="Address..." />
      <input type="text" v-model="editItem.score_test" placeholder="Score Test..." />
      <input type="text" v-model="editItem.score_exam" placeholder="Score Exam..." />
      <span>Status: </span>
      <label class="toggle">
        <input type="checkbox" v-model="editItem.status" />
        <span class="slider"></span>
      </label>
      <div class="calculate-group">
        <input type="text" v-model="editItem.total_score" disabled />
        <button class="calculate-button" @click="handleCalculateScore(editItem)">Calculate</button>
      </div>
    </div>
    <button class="save-button" @click="handleSave(editItem)">Save</button>
  </div>
</template>

<script>
export default {
  name: "EditClass",
  props: {
    item: Object,
  },
  data() {
    return {
      editItem: {},
    };
  },
  watch: {
    item: {
      handler: function(newQuestion) {
        this.editItem = this.cloneItem(newQuestion);
      },
      deep: true,
    },
  },
  methods: {
    cloneItem(item) {
      return JSON.parse(JSON.stringify(item));
    },
    handleSave(item) {
      console.log(item)
      this.$emit("save", item);
      this.editItem = {};
    },
    closeEdit(){
      this.editItem = this.item;
      this.$emit("close");
    },
    handleCalculateScore(item) {
      if (item.score_test && item.score_exam) {
        this.editItem.total_score = (parseInt(item.score_test) + parseInt(item.score_exam)) / 2;
      } else {
        this.editItem.total_score = 0;
      }
    },
  },
};
</script>