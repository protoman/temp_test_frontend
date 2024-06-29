<template>
  <div class="editActivity">
    <h1>Edit Activity</h1>
    <h3>
    <form>
        Client:
        <select>
            <item v-for="item in clientList" :key="item.id" :value="activity.clientId">{{ item.id }} - {{ item.name }}</item>
        </select>
        Project:
        <select>
            <item v-for="item in projectList" :key="item.id" :value="activity.projectId">{{ item.id }} - {{ item.name }}</item>
        </select>
        Name: <input type="text" name="username" v-model="activity.name">
        <button @click="save">
    </form>
    </h3>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .editActivity {
    min-height: 100vh;
    align-items: center;
  }
}
</style>

<script>
import axios from 'axios'

const items = ref([{ id: 1, name: 'Foo' }, { id: 2, name: 'Bar' }])
const activityId = 1;

console.log(this.$route.query.test);

export default {
  name: 'editActivity',
  data() {
    return {
      projectList: [],
      clientList: [],
      activity: {
          clientId: 0,
          projectId: 0,
          name: ""
      }
    }
  },
  created() {
    this.getProjectList();
    this.getClientList();
    this.getActivityById(activityId);
  },
  methods: {
    getProjectList() {
      axios
        .get('http://localhost:8080/api/v1.0/practice/project')
        .then((res) => {
          this.projectList = res.data
        })
        .catch((error) => {
          console.log(error)
        })
    },

    getClientList() {
      axios
        .get('http://localhost:8080/api/v1.0/practice/client')
        .then((res) => {
          this.clientList = res.data
        })
        .catch((error) => {
          console.log(error)
        })
    },

    getActivityById(id) {
        if (id == null) {
            return {
                clientId: 0,
                projectId: 0,
                name: ""
            };
        }
      axios
        .get('http://localhost:8080/api/v1.0/practice/activity/id/' + id)
        .then((res) => {
          this.activity = res.data
        })
        .catch((error) => {
          console.log(error)
        })
    },

    save() {
      axios
        .post('http://localhost:8080/api/v1.0/practice/activity/', this.activity)
        .then((res) => {
          this.activity = res.data
        })
        .catch((error) => {
          console.log(error)
        })

    }
  }
}
</script>
