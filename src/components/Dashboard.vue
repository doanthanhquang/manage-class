<template>
  <div class="container">
    <div class="header">
      <h1 class="title">Manage Scores</h1>
      <div class="search-group">
        <select v-model="filter" class="search-input">
          <option value="" selected>All</option>
          <option :value="true">True</option>
          <option :value="false">False</option>
        </select>
      </div>
      <button class="create-button" @click="isCreate = true, isView = false, isDelete = false, isEdit = false">Create</button>
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
          <template v-if="!filter && filter!==false">
            <tr v-for="item in items" :key="item.id">
              <td>{{ item.id }}</td>
              <td>{{ item.name }}</td>
              <td>
                <label class="toggle">
                  <input type="checkbox" v-model="item.status" />
                  <span class="slider"></span>
                </label>
              </td>
              <td>{{ item.score_test }}</td>
              <td>{{ item.score_exam }}</td>
              <td>{{ item.address }}</td>
              <td>{{ item.total_score }}</td>
              <td>
                <button class="action-button view-button" @click="handleView(item)">View</button>
                <button class="action-button edit-button" @click="handleEdit(item)">Edit</button>
                <button class="action-button delete-button" @click="handleDelete(item)">Delete</button>
              </td>
            </tr>
          </template>
          <template v-else>
            <tr v-for="item in items" :key="item.id">
              <template v-if="filter == item.status">
                <td>{{ item.id }}</td>
                <td>{{ item.name }}</td>
                <td>
                  <label class="toggle">
                    <input type="checkbox" v-model="item.status" />
                    <span class="slider"></span>
                  </label>
                </td>
                <td>{{ item.score_test }}</td>
                <td>{{ item.score_exam }}</td>
                <td>{{ item.address }}</td>
                <td>{{ item.total_score }}</td>
                <td>
                  <button class="action-button view-button" @click="handleView(item)">View</button>
                  <button class="action-button edit-button" @click="handleEdit(item)">Edit</button>
                  <button class="action-button delete-button" @click="handleDelete(item)">Delete</button>
                </td>
              </template>
            </tr>
          </template>
        </tbody>
      </table>
    </div>
    <div class="create-popup" :class="{ active: isCreate }">
      <create-class @close="isCreate = false" @save="saveCreate" />
    </div>
    <div class="create-popup" :class="{ active: isEdit }">
      <edit-class @close="isEdit = false" :item="item" @save="saveEdit"/>
    </div>
    <div class="create-popup" :class="{ active: isView }">
      <view-class @close="isView = false" :item="item"/>
    </div>
    <div class="create-popup" :class="{ active: isDelete }">
      <delete-class @close="isDelete = false" @delete="deleteItem"/>
    </div>
  </div>
</template>

<script>
import CreateClass from "@/components/CreateClass.vue";
import EditClass from "@/components/EditClass.vue";
import ViewClass from "@/components/ViewClass.vue";
import DeleteClass from "@/components/DeleteClass.vue";

export default {
  name: "Dashboard",
  components: { CreateClass, EditClass, ViewClass, DeleteClass },
  data() {
    return {
      item: {},
      filter: '',
      isCreate: false,
      isEdit: false,
      isDelete: false,
      isView: false,
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
  methods: {
    saveCreate(item) {
      this.items.push(item);
      this.isCreate = false;
    },
    saveEdit(itemEdit) {
      this.items = this.items.map((item) => {
        if (item.id === itemEdit.id) {
          return itemEdit
        }
        return item;
      });
      this.isEdit = false;
    },
    handleEdit(item) {
      this.isEdit = true;
      this.isView = false;
      this.isCreate = false;
      this.isDelete = false;
      this.item = item;
    },
    handleView(item){
      this.isEdit = false;
      this.isView = true;
      this.isCreate = false;
      this.isDelete = false;
      this.item = item;
    },
    handleDelete(item){
      this.isEdit = false;
      this.isView = false;
      this.isCreate = false;
      this.isDelete = true;
      this.item = item;
    },
    deleteItem() {
      this.items = this.items.filter((item) => item.id!== this.item.id);
      this.isDelete = false;
    }
  },
};
</script>
