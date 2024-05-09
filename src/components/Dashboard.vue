<template>
  <div class="container">
    <div class="header">
      <h1 class="title">Manage Scores</h1>
      <div class="search-group">
        <input type="text" class="search-input" placeholder="Search..." />
        <button class="filter-btn">Search</button>
      </div>
      <button class="create-button">Create</button>
    </div>
    <div class="form-container">
      <table class="form-table">
        <thead>
          <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Status</th>
            <th>Test Score</th>
            <th>Exam Score</th>
            <th>Address</th>
            <th>Total Score</th>
            <th>Action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in items" :key="item.id">
            <td>{{ item.id }}</td>
            <td>{{ item.name }}</td>
            <td>
              <label class="toggle">
                <input type="checkbox" />
                <span class="slider"></span>
              </label>
            </td>
            <td>{{ item.score_test }}</td>
            <td>{{ item.score_exam }}</td>
            <td>{{ item.address }}</td>
            <td>{{ item.total_score }}</td>
            <td>
              <button class="action-button view-button">View</button>
              <button class="action-button edit-button">Edit</button>
              <button class="action-button delete-button">Delete</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="create-popup">
      <create-class />
    </div>
  </div>
</template>

<script>
import CreateClass from "@/components/CreateClass.vue";

export default {
  name: "Dashboard",
  components: { CreateClass },
  data() {
    return {
      items: [
        {
          id: 1,
          name: "Nguyen Hoang An",
          status: true,
          score_test: 8,
          score_exam: 7,
          address: "Sofa, 15/20 Street 8, Truong Tho Ward, Thu Duc, Ho Chi Minh City",
          total_score: 7.5,
        },
        {
          id: 2,
          name: "Nguyen Thi Thanh Hang",
          status: true,
          score_test: 10,
          score_exam: 10,
          address: "720A D. Dien Bien Phu, Vinhomes Tan Cang, Binh Thanh, Ho Chi Minh City 72300",
          total_score: 10,
        },
        {
          id: 3,
          name: "Doan Thanh Quang",
          status: false,
          score_test: 8,
          score_exam: 8,
          address: "1st floor, 15/20 Street 8, Truong Tho Ward, Thu Duc, Ho Chi Minh City",
          total_score: 8,
        },
      ],
    };
  },
};
</script>

<style scoped>
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
</style>
