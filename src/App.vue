<template>
  <div id="app">
    <dashboard />
  </div>
</template>

<script>
import Dashboard from "@/components/Dashboard";

export default {
  name: "App",
  components: {
    Dashboard,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.container {
  font-family: Arial, sans-serif;
  max-width: 1300px;
  margin: 0 auto;
  padding: 20px;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
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
.close {
  background-color: #4caf50;
  color: white;
  border: none;
  padding: 10px 20px;
  margin-right: 30px;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.close:hover {
  background-color: #45a049;
}

.delete-button {
  background-color: red;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  opacity: 0.8;
  transition: background-color 0.3s ease;
}

.delete-button:hover {
  opacity: 1;
}
.title {
  font-size: 24px;
}

.create-button {
  background-color: #4caf50;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
}

.form-container {
  overflow-x: auto;
}

.form-table {
  width: 100%;
  border-collapse: collapse;
}

.form-table th,
.form-table td {
  border: 1px solid #ddd;
  padding: 8px;
  text-align: left;
}

.form-table th {
  background-color: #f2f2f2;
}

.action-button {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 8px 12px;
  border-radius: 4px;
  cursor: pointer;
  margin-right: 5px;
}

.view-button {
  background-color: #17a2b8;
}

.edit-button {
  background-color: #ffc107;
}

.delete-button {
  background-color: #dc3545;
}
.form-table th {
  text-align: center;
}

.form-table td {
  text-align: left;
}
.form-table td:nth-child(1) {
  text-align: center;
}
.form-table td:nth-child(3) {
  text-align: center;
}
.form-table td:nth-child(4) {
  text-align: center;
}
.form-table td:nth-child(5) {
  text-align: center;
}
.form-table td:nth-child(6) {
  max-width: 300px;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.form-table td:nth-child(7) {
  text-align: center;
}
.form-table td:nth-child(8) {
  text-align: center;
}
.filter-btn {
  margin-left: 5px;
}
.search-group {
  display: flex;
  align-items: center;
}

.search-input {
  flex: 1;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-right: 10px;
}

.filter-btn {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 8px 12px;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.filter-btn:hover {
  background-color: #0056b3;
}
.create-popup {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: white;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 20px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  z-index: 999;
  display: none;
}

.create-popup.active {
  display: block;
}

</style>
