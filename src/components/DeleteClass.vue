<template>
  <div class="create-class-container">
    <button class="close-button" @click="$emit('close')">X</button>
    <h2>Delete Class</h2>
    <div class="input-group">
      <span>Bạn có chắc chắn muốn xoá?</span>
    </div>
    <button class="close" @click="$emit('close')">Close</button>
    <button class="delete" @click="$emit('delete')">Delete</button>
  </div>
</template>

<script>
export default {
  name: "DeleteClass",
};
</script>
