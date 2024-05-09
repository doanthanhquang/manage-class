<template>
  <div class="create-class-container">
    <button class="close-button">X</button>
    <div class="input-group">
      <input type="text" placeholder="Name..." />
      <input type="text" placeholder="Address..." />
      <input type="text" placeholder="Score Test..." />
      <input type="text" placeholder="Score Exam..." />
      <span>Status: </span>
      <label class="toggle">
        <input type="checkbox" />
        <span class="slider"></span>
      </label>
      <div class="calculate-group">
        <input type="text" disabled />
        <button class="calculate-button">Calculate</button>
      </div>
    </div>
    <button class="save-button">Save</button>
  </div>
</template>

<script>
export default {
  name: "CreateClass",
};
</script>

<style scoped>
.create-class-container {
  max-width: 300px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f9f9f9;
  position: relative;
}

.close-button {
  position: absolute;
  top: 10px;
  right: 10px;
  background: none;
  font-size: 16px;
  cursor: pointer;
  color: #f00;
  border: 1px solid #f00;
  width: 24px;
  height: 24px;
  transition: color 0.3s ease;
}

.close-button:hover {
  color: #555;
  border-color: #f55;
}

.input-group {
  margin-bottom: 15px;
  margin-top: 15px;
}

.input-group input[type="text"] {
  width: calc(100% - 10px);
  padding: 10px;
  margin-bottom: 10px;
  margin-top: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-sizing: border-box;
}

.save-button {
  background-color: #4caf50;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.save-button:hover {
  background-color: #45a049;
}
.toggle {
  position: relative;
  display: inline-block;
  width: 40px;
  height: 20px;
}

.toggle input[type="checkbox"] {
  opacity: 0;
  width: 0;
  height: 0;
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 34px;
}

.slider:before {
  position: absolute;
  content: "";
  height: 16px;
  width: 16px;
  left: 2px;
  bottom: 2px;
  background-color: white;
  -webkit-transition: 0.4s;
  transition: 0.4s;
  border-radius: 50%;
}

input[type="checkbox"]:checked + .slider {
  background-color: #4caf50;
}

input[type="checkbox"]:focus + .slider {
  box-shadow: 0 0 1px #4caf50;
}

input[type="checkbox"]:checked + .slider:before {
  -webkit-transform: translateX(20px);
  -ms-transform: translateX(20px);
  transform: translateX(20px);
}
.calculate-group {
  display: flex;
  align-items: center;
}

.calculate-group input[type="text"] {
  flex: 1;
  margin-right: 10px;
}

.calculate-button {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.calculate-button:hover {
  background-color: #0056b3;
}
</style>
