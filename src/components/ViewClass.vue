<template>
  <div class="create-class-container">
    <button class="close-button" @click="$emit('close')">X</button>
    <h2>View Class</h2>
    <div class="input-group">
      <input type="text" v-model="item.name" disabled placeholder="Name..." />
      <input type="text" v-model="item.address" disabled placeholder="Address..." />
      <input type="text" v-model="item.score_test" disabled placeholder="Score Test..." />
      <input type="text" v-model="item.score_exam" disabled placeholder="Score Exam..." />
      <span>Status: </span>
      <label class="toggle">
        <input type="checkbox" v-model="item.status" disabled/>
        <span class="slider"></span>
      </label>
      <div class="calculate-group">
        <input type="text" v-model="item.total_score" disabled />
        <button class="calculate-button">Calculate</button>
      </div>
    </div>
    <button class="save-button" disabled>Save</button>
  </div>
</template>

<script>
export default {
  name: "ViewClass",
  props: {
    item: Object,
  }
};
</script>