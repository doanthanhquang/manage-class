<template>
  <div class="create-class-container">
    <button class="close-button" @click="$emit('close')">X</button>
    <h2>Create Class</h2>
    <div class="input-group">
      <input type="text" v-model="item.name" placeholder="Name..." />
      <input type="text" v-model="item.address" placeholder="Address..." />
      <input type="text" v-model="item.score_test" placeholder="Score Test..." />
      <input type="text" v-model="item.score_exam" placeholder="Score Exam..." />
      <span>Status: </span>
      <label class="toggle">
        <input type="checkbox" v-model="item.status"/>
        <span class="slider"></span>
      </label>
      <div class="calculate-group">
        <input type="text" v-model="item.total_score" disabled />
        <button class="calculate-button" @click="handleCalculateScore(item)">Calculate</button>
      </div>
    </div>
    <button class="save-button" @click="handleSave(item)">Save</button>
  </div>
</template>

<script>
export default {
  name: "CreateClass",
  data() {
    return {
      item: {
        id: null,
        name: "",
        status: false,
        score_test: null,
        score_exam: null,
        address: "",
        total_score: null,
      },
    };
  },
  methods: {
    handleSave(item) {
      this.$emit("save", item);
      this.item = {
        id: null,
        name: "",
        status: false,
        score_test: null,
        score_exam: null,
        address: "",
        total_score: null,
      };
    },
    handleCalculateScore(item) {
      if (item.score_test && item.score_exam) {
        this.item.total_score =
          (parseInt(item.score_test) + parseInt(item.score_exam)) / 2;
      } else {
        this.item.total_score = 0;
      }
    }
  },
};
</script>
